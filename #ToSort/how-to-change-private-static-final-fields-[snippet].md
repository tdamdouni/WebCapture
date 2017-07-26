# How to Change Private Static Final Fields [Snippet]

_Captured: 2017-04-20 at 23:54 from [dzone.com](https://dzone.com/articles/how-to-change-private-static-final-fields?edition=292902&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-20)_

Microservices! They are everywhere, or at least, the term is. [When should you use a microservice architecture? What factors should be considered when making that decision? Do the benefits outweigh the costs? Why is everyone so excited about them, anyway?](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D) Brought to you in partnership with [IBM](https://dzone.com/go?i=180128&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943538%26PluID%3D0%26ord%3D%255Btimestamp%255D).

Sometimes you need dirty hacks. This is one that can be useful in testing scenarios -- how to change fields that are not meant to be changed.

If we have class `Knowledge` with the answer for everything:

```
public class Knowledge {
    private static final Integer ANSWER = 42;
    public String askQuestion(String question) {
        return "The answer to '" + question + "' is: " + ANSWER;
    }
}
```


We now want to change the answer for testing purposes:

```
public class KnowledgeTest {
    @Test
    public void testAskQuestion() throws Exception {
        Knowledge knowledge = new Knowledge();
        String answer = knowledge.askQuestion("question?");
        assertThat(answer, is("The answer to 'question?' is: 42"));
        setFinalStaticField(Knowledge.class, "ANSWER", 41);
        answer = knowledge.askQuestion("question?");
        assertThat(answer, is("The answer to 'question?' is: 41"));
    }
    private static void setFinalStaticField(Class<?> clazz, String fieldName, Object value)
            throws ReflectiveOperationException {
        Field field = clazz.getDeclaredField(fieldName);
        field.setAccessible(true);
        Field modifiers = Field.class.getDeclaredField("modifiers");
        modifiers.setAccessible(true);
        modifiers.setInt(field, field.getModifiers() & ~Modifier.FINAL);
        field.set(null, value);
    }
}
```

We make this possible by setting the field to accessible and removing the `final` modifier. Then the field can be set using reflection.

Please use this with care and only in test scopes. Also, for primitive types the compiler makes use of constant folding -- then such a solution has no effect.

Happy (dirty) hacking!

Discover how the Watson team is [further developing SDKs in Java](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D), Node.js, Python, iOS, and Android to access these services and make programming easy. Brought to you in partnership with [IBM](https://dzone.com/go?i=180126&u=https%3A%2F%2Fbs.serving-sys.com%2Fserving%2FadServer.bs%3Fcn%3Dtrd%26mc%3Dclick%26pli%3D20943536%26PluID%3D0%26ord%3D%255Btimestamp%255D).
