# July in IoT: The Tinkerer's Edition

_Captured: 2018-07-31 at 22:39 from [dzone.com](https://dzone.com/articles/july-in-iot-the-tinkerers-edition?edition=385308&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-31)_

Happy July, everyone! It's that time of the month again, so let's look at what you prototypers and DIYers have been interested in on DZone in the past 30 days or so as well as some news from around the Internet.

This month's post probably could have been subtitled "Doing Cool Things With a Raspberry Pi," but between you and me, I like the branding of "The Tinkerer's Edition."

Anyway, check out how you can run the TICK Stack on a Pi, how to build a weather station, and see how microservices and IoT are pushing each other forward.

Also, if you know a fair bit about MQTT and/or IIoT, please check out the bottom of this post for some paid writing opportunities!

## Connecting You With What's Cool

  1. [Setting Up a Raspberry Pi SD Card With Amateur Radio-Related Apps](https://dzone.com/articles/setting-up-a-raspberry-pi-sd-card-with-some-amateu), by [Kevin Hooke](https://dzone.com/users/273254/khooke.html). Want help setting up radio-related apps? Click here to learn more about setting up a Raspberry Pi SD card with amateur radio-related apps.
  2. [Eclipse Debugging With Pointers and Arrays](https://dzone.com/articles/eclipse-debugging-with-pointers-and-arrays), by [Erich Styger](https://dzone.com/users/1010735/StonehillRitschi.html). In this tutorial, we will show you how to effectively debug pointers and arrays in C using the Eclipse IDE.
  3. [How to Run the TICK Stack on a Raspberry Pi](https://dzone.com/content/2319973/edit.html), by [Noah Crowley](https://dzone.com/users/3160523/noahcrowley.html). Click here to learn how to use and install the TICK Stack on a Raspberry Pi, along with important points to consider while operating the stack.
  4. [How to Build Your Own Weather Station Using a Raspberry Pi](https://dzone.com/articles/how-to-build-your-own-weather-station-using-a-rasp), by [Austin Spivey](https://dzone.com/users/3160867/anspivey.html). Have you ever wanted to create your own weather station? Now, you can! Click here to learn more about building a weather station with a Raspberry Pi.
  5. [How We Developed a System to Support IoT Payments at Hong Kong Hackathon (Part 1)](https://dzone.com/articles/how-we-developed-a-system-to-support-iot-payments) and [(Part 2)](https://dzone.com/articles/how-we-developed-a-system-to-support-iot-payments-1), by [Alexey Makeev](https://dzone.com/users/3362866/therealal.html). Want to learn how these two developers developed a system to support IoT payments at this year's Hackathon in Hong Kong? Click here to learn more!

By the way, if you're interested in writing for your fellow DZoners, feel free to check out our [Writers' Zone](http://dzone.com/writers-zone), where you can also find some current [hot topics](https://dzone.com/articles/dzone-writing-prompts-and-hot-topics) and our [Bounty Board](http://bounty.dzone.com/), which has writing prompts coupled with prizes.

## IoT Around the Web

### Microservices and IoT

It's hard to find a pair of trends hotter in the IT space right now than IoT and microservices. With that in mind, [here's a great write-up](https://sdtimes.com/micro/why-microservices-will-drive-enterprise-grade-iot-for-business/) from SD Times that showcases the synergy between these two trends and how microservices can enhance IoT development.

### Looks Like Fog (Computing) Outside!

Fog computing has been a known entity for a while, but if you're just getting into the edge of IoT, [here's a good breakdown](https://www.nojitter.com/post/240173671/iot-forecast-foggy-with-a-chance-of-clouds) of fog computing and what it brings to your systems.

### Build Your Own Smart Camera

And now for my compulsory "cool IoT project" entry. There's no shortage of uses for a smart camera, so if you're interested, [here's a start-to-finish guide](https://electronicsforu.com/electronics-projects/iot-based-smart-camera-using-android-raspberry-pi) to getting one set up and coded!

## Make Money

And now, as promised, here are a couple of [publications](https://dzone.com/refcardz) we would love to have updated! If you've got subject matter expertise and want to make some cash, feel free to email us at editors@dzone.com.

  


On June 10th, it was the third day in Hong Kong. In the previous 26 hours, we had almost given up sleep, trying to develop the prototype for a project codenamed SensorPay, as part of the first stage of EOS Global hackathon with a prize fund of 1.5 million USD. The moment to introduce our project to the judge was approaching.

If you are eager to hear the end of the story, you can simply jump right to the last chapter. In our last post, we began our story about EOS technologies and how we came about this idea of linking IoT payments to EOS. In this installment, we will describe the technical content of our project in greater detail.

Smart Contracts

### Supplier Contract and Energy Consumption Billing

After the hackathon started, we began outlining a contract structure based on the above schema. The system included the following contracts:

  * `supplier` -- supplier contract;

  * `billing_electricity` -- a contract to calculate payments for energy consumption per each counter tick.

Standard CRUD transactions play a major role in a `supplier` contract, adding users, rates, counters, or subtracting funds from the user's balance. More sophisticated methods were used to control the receipt of data sent by counters, calling a contract for payment calculation (billing) and charging funds from an individual user account after a callback from the billing contract. An appropriate billing contract was selected based on a user base rate.

After the method is called, payment was calculated in a billing contract and a method was called to charge the payment amount from an individual user account. After setting up a basic logic, we even had some doubts about whether our contracts were too simplistic. A bit later, after we deployed contracts in the node and tested them, it became perfectly clear that the contracts might be simplistic, of course, but there were still some subtle aspects.

After deployment, we saw that the expected way to call a contract from another contract was not functioning, because the required permissions were missing. Unlike smart contracts in Ethereum where a contract is called from another contract on behalf of a calling contract, in EOS, the entire sequence starts from the transaction initiator. When calling a contract from another contract, a check is performed to see whether the initiator permitted the contract to do so.

Mentors immediately gave us a hint on what we had to do in this simple case. Permissions are added as follows (by calling an eosio system smart contract):
    
    
    ./cleos push action eosio updateauth '{"account":"electricity","permission":"active","parent":"owner","auth":{"keys":[{"key":"EOS7oPdzdvbHcJ4k9iZaDuG4Foh9YsjQffTGniLP28FC8fbpCDgr5","weight":1}],"threshold":1,"accounts":[{"permission":{"actor":"supplier","permission":"eosio.code"},"weight":1}],"waits":[]}}' -p electricity

In this case, the `electricity` account permits the `supplier` contract to call other contracts on its behalf. To learn more about permissions, go to [Technical WP EOS](https://github.com/EOSIO/Documentation/blob/master/TechnicalWhitePaper.md). In our implementation, the `supplier` contract, called the `billing` contract, and the `billing` contract, in its turn, again called the `supplier` contract. However, when we tried to add permissions in a similar way, it just did not work.
    
    
    ./cleos push action eosio updateauth '{"account":"electricity","permission":"active","parent":"owner","auth":{"keys":[{"key":"EOS7oPdzdvbHcJ4k9iZaDuG4Foh9YsjQffTGniLP28FC8fbpCDgr5","weight":1}],"threshold":1,"accounts":[{"permission":{"actor":"supplier","permission":"eosio.code"},"weight":1},{"permission":{"actor":"billelectro","permission":"eosio.code"},"weight":1}],"waits":[]}}' -p electricity

The following error message appeared --"Invalid authority." And, in this case, the mentors could not help us. They confessed that they had never faced such an issue. Who had done something like this? Probably, only Dan Larimer. We failed to promptly detect a reason for this error in EOS code and even started thinking of some alternative solutions that would not use any call chains. We could not get it right because of the difference between call engines in other EOS contracts and in Ethereum. When calling another contract, the call is added to a queue and will only be processed after the current call. This prevents calling the contract and reading the data recorded by this contract.

Later, with help of examining EOS code, we managed to determine the reason for the error. It turned out that accounts in the permission list needed to be sorted by account: _Make sure all keys are unique and sorted and all account permissions are unique and sorted_ ([authority.hpp](https://github.com/EOSIO/eos/blob/v1.0.5/libraries/chain/include/eosio/chain/authority.hpp#L139)). After re-ordering the accounts permission update was successfully applied, our contract system became functional.

### Problem With Memory Handling C Functions

Funny enough, we could not use ready number parsing functions (!) for reading the billing configuration. The `std::istringstream` class required the `env.calloc` symbol during linking in nodeos environment, which was rather weird. When `atof`, `sscanf,` and similar functions were used, `env.realloc` dependency came up. For some reason, the above memory handling functions in a standard C library could not be found in the course of loading code in nodeos. However, memory handling C++ functions were fully functional.

Of course, during the execution of a WebAssembly contract, an individual "sandbox" provided for each transaction (subject to conditions) is used instead of a standard memory allocator. Support for memory handling C functions is also implemented on top of this sandbox. The implementations of these functions are available in [EOS standard contracts](https://github.com/EOSIO/eos/blob/v1.0.1/contracts/eosiolib/eosiolib.cpp#L554). This means that something was probably wrong at the linking step.

After spending an hour trying to find a solution together with one of the mentors, we decided to go the other way and develop a workaround. We decided to write our own code to complete the number parsing task. The datastream EOS framework wasn't suitable for us; we needed an opportunity to save data packages with various structures in a single field and create them manually (the billing system configurations).

### Billing of the Purchased Items

Then, we got a second wind -- either due to energy drinks or to an early breakfast -- and we managed to write a [billing system](https://github.com/smartzplatform/eos-hackathon/commit/08e541f85680dae27996df2093a51049f4b7caa7) for shop purchases. The general workflow was as follows:

  1. The supplier creates a billing contract and registers it in their general contract.

  2. The supplier installs the RFID-reading and EOS-connected gate at the store's exit, and the gate is assigned its own account registered in a billing contract.

  3. Each item in the store is equipped with an RFID tag, and all the tags are registered in a billing contract.

  4. A buyer pays for the purchased item by scanning its RFID tag, and the item is then removed from the billing contract.

  5. When the buyer goes out of the store, the gate again reads RFID tags of the purchased items. If the item is still registered in the store, the transaction does not pass, and the gate issues an alarm (actually, there is no need to send transactions, it is enough just to read the table).

It makes no sense to dwell on the code of contracts. This is a standard C++14 with a number of EOS-specific structures and libraries. To learn more, go to [EOSIO Wiki](https://github.com/EOSIO/eos/wiki) and [EOSIO Developer Portal](https://developers.eos.io/).

### Front-end

The front-end portion of the project was implemented based on React. Instead of the familiar Redux, we decided to use MobX, which helped to significantly accelerate the development process and enable simple and easy management of the global state.

Front-blockchain integration did not go as smoothly as expected. The [eosjs](https://github.com/EOSIO/eosjs) package is extensively evolving along with the EOS wallet for the [Scatter](https://github.com/EOSEssentials/Scatter) web browser. In this combination, it may be quite troublesome. And, there is no guarantee that the code that worked fine yesterday will keep on working today. This was exactly our mistake (and to tell you the truth, we were making it repeatedly). After another hour of effort and debugging while we were already half-asleep, the problem was successfully solved.

Let us have a look at a simplified interface schema for the client portion of the EOS application. We will need an eosjs library and a Scatter browser plugin for this purpose.

It is worth bearing in mind that Scatter is intensely upgraded along with eosjs, so do not forget to update the library regularly.

Let us take a quick look at the read and write capabilities. There are two methods of communication with smart contracts in EOS: sending transactions (which calls a blockchain modification without returning any values) and reading tables (a read-only action).

Let us have a look at the code for sending a transaction:
    
    
        .then(() => this.scatter.getIdentity({ accounts: [this.network] }))
    
    
            const eos = this.scatter.eos(this.network, Eos, this.configEosInstance);
    
    
            return eos.transaction(accountName, (contract) => {

Input arguments are the name of the function, object, and its values are arguments for this function. In the third line, we confirm the particular EOS network we are using. For the fourth line, we get the `identity`. Here, the parameter is an object containing the `accounts` field (for this network). `getAccountName` function returns the first account from the obtained list of accounts (in `identity` object).

In this example, Scatter is used to sign the transaction. Scatter is a sort of an envelope covering an `Eos` class instance. In the ninth line, we call an `eos` method with the following parameters:

  1. `this.network` -- an object with the network parameters

  2. `Eos` -- an eosjs instance

  3. `this.configEosInstance` -- an object containing parameters for an Eos instance (see the eosjs documentation)

The last method, `transaction`, accepts input `accountName` and `callback`. The `callback` argument is a contract residing in the `accountName` account. In the `callback`, we call the obtained contract's method with an object, and its keys are the arguments for the called method.

Let's have a look at the table reading method:

Here, we only need an `eos` instance to perform the reading.

We decided not to use Materialize, Semantic, or Ant for the interface decoration. But, instead, we threw together our own styles. During the last hours of the hackathon, we got struck by an idea -- we need to add process visualization. We used green to highlight new rows in the tables for a couple of seconds and made a cool effect like with the display of stock exchange data. This improvement made our project far more attractive and became the last step in building our UI.

## Assembling

Three hours before the end of the hackathon, we already had Raspberry Pi with the Mercury energy consumption counter, an RFID reader connected to it, and LED indication. The entire energy flow at the table was passing through Mercury. Raspberry Pi sent transactions to our blockchain for each 0.3125 Wh spent and for each "purchase." The supplier could manage users, sensors, and billing, as well as view the consumption statistics.

![Image title](https://dzone.com/storage/temp/9662367-y6uqmz1upvprppiimceoecejewg.jpeg)

We spent another hour testing and adding the finishing touch. Two hours before the time was up, we had already got a comprehensive product with two implemented use cases that became a perfect illustration for the concept -- and no last-minute commits!

## Demonstration

Project demonstrations (aka pitches) consist of two steps. At the first step, 69 participating teams were divided into four groups, and the groups were each presenting their projects on an individual basis to two judges only. Judges assigned their scores (four criteria, 5 points each) and based it on the scores. The top 10 teams were selected to participate in the second round. These teams got an opportunity to introduce their projects on a big stage to the audience and the entire jury of eight judges.

We were in the first group, and our judges were the CEO and President of Everipedia (I wonder what the difference is between these two positions?). Each pitch had a time limit (max. 3 minutes), that was strictly monitored with a timer. We even managed to finish our impressive -- though a bit inconsistent -- presentation 30 seconds before the time was up. The judges briefly asked a couple of clarification questions, and our presentation was over.

We were naive enough to be surprised by the fact that even our product's operating capability (let alone the code) was completely ignored by the judges. Implementation-related technical issues were not even of the slightest interest to them. We could have just shown blinking LEDs on Raspberry Pi with some pictures at the front, and got the same reaction, I suppose.

So, we had the impression that our project presentation was a complete fail because we were hoping to make a strong impression with our actual solution and prototype, and not with a mere emotional description of a socially meaningful and ambitious project. Our presentation was rendered with clockwork precision: we described the problem, pain points, and our solution, we showed how it all works and spoke of our plans for further project improvement. If we had only known how the assessment works, we would probably have done it all some other way.

The judges watched the presentations of the four groups in the first round shared their scores and opinions with each other for 15 minutes following the presentations. After that, they began announcing the winners. The audience was quite nervous: after surviving a 26-hour marathon, people just wanted to win; plenty of strong teams were quite sure they could claim the award. We knew that too -- and were patiently waiting for the results.

To keep the audience on their toes, the jury announced the winners in three steps. First, they announced only four finalists, then -- three more finalists, and finally -- the last three. The announcements were interspersed with on-stage performances, and after the last announcement, there was a final performance. We did not make it into the top 10, and we did not get a chance to go up on the big stage. The top 10 included two Russian-speaking teams though, and one of them took 3rd place. Our congratulations to the winners -- their rewards were well-deserved.

See the project demonstration on [YouTube](https://www.youtube.com/watch?v=GVG_bYzvfZk).

## 5\. Conclusion and Future Plans

AngelHack team, the organizers of the hackathon, did a brilliant job. The hackathon was top-notch; it all went almost flawless. Our personal reward was an amazing journey, tons of learning experience and the opportunity to get in touch with the strongest developers and mentors. Yes, we probably expected a more technical assessment, but whatever the case, we realized that our chance to win was just a chance.

In only 26 hours, we managed to create a fully-functional framework model for processing IoT payments via EOS blockchain. We are extremely proud of this result, and we are completely sure that it is valuable, applicable and scalable.

Our further plans include adding a comprehensive convenient UI (and we can leverage our cross-blockchain [Smartz](https://smartz.io/) platform) and elaborating some specific use cases. If any of you happen to know how to set up a mass production of blockchain-ready energy, water, and gas consumption counters, you are welcome to contact us, we will be happy to discuss your ideas :)

Based on some insider information, we could approximately estimate that in many countries thousands of people are checking and adjusting the utility bills virtually manually. At a rough estimate, our system will help save billions of dollars annually for this type of labor costs -- let alone saving millions of nerve cells of those poor people. So I guess that installation of our solution with a codename of SensorPay to your electrical distribution boards is right on its way!

The project team and co-authors of this article:

  * Yury Vasilchikov (entrepreneur)

  * Alghys Iyevlev (hardware & backend developer)

  * Aleksey Makeyev (architect, backend developer, devops)

  * Vyacheslav Melnikov (frontend developer)

  * Vladimir Khramov (blockchain & backend developer)
