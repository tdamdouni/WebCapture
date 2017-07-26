# Loosely Coupled Tests

_Captured: 2015-10-17 at 22:10 from [blog.8thlight.com](http://blog.8thlight.com/chris-jordan/2015/08/26/loosely-coupled-testing.html)_

Test Driven Development (TDD) has a plethora of benefits, but the one that stands out for me is how it helps to unify a team. This is because the outcome of TDD is a code base with high test coverage that acts as a safety net for future changes.

However, there is a risk that this safety net can become too tightly entangled around our code. For example, overusing mocking libraries or unit tests that are too knowledgeable about the code they are checking can in fact make the code more cumbersome to work with. Because software is in a perpetual state of flux--either due to new features being added or issues with the current code being addressed--our tests need to allow for change.

# Mocking Collaborators

One of the fundamental axioms of object-oriented programming is that a set of objects work together in order to achieve a particular goal. This has a profound effect on how we do our testing. When we are writing a test for a class `X` that depends on class `Y`, then the unit test for class `X` also needs to be aware of this dependency.

Let us imagine we are working on an `ATM` class that models a cash machine, which you can use to extract money from, view bank balances, and so on. Our `ATM` class is going to be interacting with the `Bank`.

Unfortunately, the `Bank` communicates directly to various external systems, so we can't easily use the real `Bank` class in the unit test for our `ATM`. Instead, we will be utilizing polymorphism and dependency injecting test doubles of `Bank` into `ATM`.

There are a few ways to create test doubles, but the more common way that I have observed is to use a mocking library (e.g. JMock/Mockito for Java, rspec-mocks for Ruby). The reason why this approach is so common is because it is relatively quick and easy to do. For example, to stub out the bank into returning bank account details for a particular bank account, we can do something as follows:
    
    
    it 'shows balance' do
      expect(test_bank).to receive(:get_account_details).and_return({balance: 0, previous_transactions = []})
      atm.show_balance
    end

This test knows a fair amount of information. It knows which methods get invoked when the `atm` is finding out the bank balance, as well the format of the response that `bank.get_account_details` generates.

It turns out that `get_account_details` method on the `Bank` is widely used across the system, and the mock setup we have used in the above test is duplicated in many places. What happens when `get_account_details` undergoes some kind of change? What happens if the return value changes from a Hash to some other data type? It is true that a lot of the production code will need changing if this were to happen, but now each test must also be painstakingly updated to incorporate the change.

Another disadvantage to using mocking libraries is the amount of test setup that they can require. It is not uncommon to see test code that relies heavily on mocking libraries to have a substantial amount of setup to ensure that all the methods on the test double have some default behaviour defined. For example, if we want to create our bank test double, we may have something as follows:
    
    
    let(:bank) { instance_double(Bank) }
    let(:atm)  { ATM.new(bank) }
    
    before do
      allow(bank).to receive(:get_account_details).and_return(balance: 20)
      allow(bank).to receive(:credit)
      allow(bank).to receive(:debit)
    end
    
    it 'displays balance' do
      expect(atm.show_balance).to eq(20)
    end
    
    it 'pays in money' do
      expect(bank).to receive(:credit).with({amount: 20, account_number: "123"})
      expect(atm.pay_cheque(20, "123"))
    end
    
    it 'extract money' do
      expect(bank).to receive(:debit).with({amount: 20, account_number: "55555 0123"})
      atm.extract_money(20))
    end

Without this default setup, we may run into errors where methods are invoked on `Bank` that have not yet been set up in the unit test. You may imagine this `before` block becoming unwieldy as bank is utilized more by `ATM`, as well as seeing this setup duplicated across other tests.

So, what is the alternative?

We can instead hand roll a `FakeBank` class that can be used across all classes.
    
    
    class FakeBank
      attr_reader :credit_transactions, :debit_transactions
    
      def get_account_details
        {balance: 0, account_number: 123456}
      end
    
      def credit(transaction)
        @credit_transactions << transaction
      end
    
      def debit(transaction)
        @debit_transactions << transaction
      end
    end

What is the advantage of doing this? Well firstly, all behaviour for our test double is now defined in one place. If we need to change the return value of `get_account_details`, we can do that change here instead of across multiple test files. Secondly, as we have complete control over this test double, we can add functionality in order to make it easier to work with in our tests. For example, we can query the `FakeBank` for the previous transactions that have been made in order to check if the ATM has debited money from a particular bank account.
    
    
    it 'debits account' do
      atm.extract_money(20)
      expect(bank.debit_transactions).to include({amount: 20})
    end

# Loosely coupled data

When we are writing unit tests, we typically want to work with some kind of data. Data manifests itself in various forms--for example, domain models, value objects, hash-maps, and so on. Data can sometimes be non-trivial to initialize--for instance, where there are many data fields required to initialize said data. To solve this problem, it is not uncommon to use test doubles that are far easier to instantiate, and then only defining pertinent fields that are required for the test to pass.

Let's say we were to create a `Transaction` data object that is to be utilized by our ATM. This can be achieved in ruby as follows:
    
    
    transaction_double = double(from_account: 123, to_account: 345, amount: 500)

The problem that I have encountered with this approach is that whenever more fields from the data object are invoked by the code under test, we have to keep adding setup behaviour to `transaction_double`. The obvious alternative is to use real objects:
    
    
    transaction = Transaction.new(id: 1, from_account: 123, to_account: 345, date: DateTime.now, amount: 500, many_more: "fields")

This is still not always ideal. Every time we want to create a `Transaction`, our tests now must have this substantial amount of initialization. Our test code is also highly dependent on the constructor not changing. Any new mandatory constructor arguments added to `Transaction` will break this test and any other tests creating `Transaction`s, whether or not those new fields being used are under test.

The best option I've found is to extract the object initialization into a separate spec helper:
    
    
    #some_bank_spec.rb
    order = create_transaction(from_account: 123, to_account: 345, amount: 500)
    
    #order_spec_helper.rb
    def create_transaction(attrs={})
      Transaction.new({id: 1, from_account: 123, to_account: 345, date: DateTime.now, amount: 500, many_more: "default fields"}.merge(attrs))
    end

Some advantages that I see with this approach are as follows:

  1. All initialization is in one place. If a new mandatory data field is added, we only have one place to make a change.

  2. In our test code, we can create a `Transaction` whereby we only need to specify the pertinent fields (if any) that we care about in the unit test. The undefined data fields take on a default value.

  3. We are allowing our code under test to interact with our real data objects just as they would do in production. Test doubles can mask issues, as the code is not being tested as thoroughly as it could be.

# In summary

Tests need to possess some knowledge about the code they are asserting in order to thoroughly test for correct behaviour and allow for change. On the other hand, too much knowledge may result in tests becoming too tightly coupled to the code, which can significantly stifle change.

Mocking libraries can be useful for quickly building a fake collaborator when duplication isn't going to be an issue and the collaborator's behaviour is simple. However, if you find that you are duplicating lots of setup in many unit tests, or your test doubles are non-trivial, then hand-rolling your test-doubles may be a better option.

When it comes to data, my advice is to always use real data objects instead of doubles created by mocking libraries whenever you can. Real data objects in your tests tend to react to change better, as there is no mock setup to maintain and it's easier to put initialization in one place.

In my experience, I've found the techniques I've just described help prevent changes in the production code from rippling too heavily into the test code. Keeping in mind the trade-offs between the various approaches and being disciplined in how you're setting up tests will be beneficial to you and your team.

#### More Posts by This Author
