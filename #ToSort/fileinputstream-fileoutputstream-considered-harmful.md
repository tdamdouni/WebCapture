# FileInputStream / FileOutputStream Considered Harmful

_Captured: 2017-04-11 at 03:53 from [dzone.com](https://dzone.com/articles/fileinputstream-fileoutputstream-considered-harmful?edition=289916&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-04-10)_

![Suricata suricatta -Auckland Zoo -group-8a \(with captions added by Stephen Connolly\)](https://www.cloudbees.com/sites/default/files/blog/2017-fileinputstream-considered-harmful.png)

Ok, so say you have been given an array of bytes that you have to write to a file. You're a Java developer. You have been writing Java code for years. You got this:

    
    
    public void writeToFile(String fileName, byte[] content) throws IOException {
        try (FileOutputStream os = new FileOutputStream(fileName)) {
            os.write(content);
        }
    }
    

  

Can you spot the bug?

What about this method to read the files back again?

    
    
    public byte[] readFromFile(String fileName) throws IOException {
        byte[] buf = new byte[8192];
        try (FileInputStream is = new FileInputStream(fileName)) {
            int len = is.read(buf);
            if (len < buf.length) {
                return Arrays.copyOf(buf, len);
            }
            ByteArrayOutputStream os = new ByteArrayOutputStream(16384);
            while (len != -1) {
                os.write(buf, 0, len);
                len = is.read(buf);      
            }
            return os.toByteArray();
        }
    } 
    



Spotted the bug yet?

Of course, the bug is in the title of this post! We are using `FileInputStream` and `FileOutputStream`.

So what, exactly, is wrong with that?

Have you ever noticed [that `FileInputStream` overrides `finalize()`](https://docs.oracle.com/javase/7/docs/api/java/io/FileInputStream.html#finalize\(\))? Same goes for `[FileOutputStream`](https://docs.oracle.com/javase/7/docs/api/java/io/FileOutputStream.html#finalize\(\)) , by the way.

Every time you create either a `FileInputStream` or a `FileOutputStream`, you are creating an object. Even if you close it correctly and promptly, it will be put into a special category that only gets cleaned up when the garbage collector does a full GC. Sadly, due to backwards compatibility constraints, this is not something that can be fixed in the JDK [anytime soon](https://bugs.openjdk.java.net/browse/JDK-8080225?focusedCommentId=13880543&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-13880543) as there _could_ be some code _out there_ where somebody has extended `FileInputStream` / `FileOutputStream` and is relying on those `finalize()` methods to ensure the call to `close()`.

Now, that is not an issue for short-lived programs… or for programs that do very little file I/O… but for programs that create a lot of files, it can cause issues. For example, [Hadoop](https://issues.apache.org/jira/browse/HDFS-8562) found "long GC pauses were devoted to process high number of final references," resulting from the creation of lots of `FileInputStream` instances.

The solution (at least if you are using Java 7 or newer) is not too hard -- apart from retraining your muscle memory -- just switch to `[Files.newInputStream(...)`](https://docs.oracle.com/javase/7/docs/api/java/nio/file/Files.html#newInputStream\(java.nio.file.Path,%20java.nio.file.OpenOption...\)) and `[Files.newOutputStream(...)`](https://docs.oracle.com/javase/7/docs/api/java/nio/file/Files.html#newOutputStream\(java.nio.file.Path,%20java.nio.file.OpenOption...\))

Our code becomes:

    
    
    public void writeToFile(String fileName, byte[] content) throws IOException {
        try (OutputStream os = Files.newOutputStream(Paths.get(fileName))) {
            os.write(content);
        }
    }
    
    public byte[] readFromFile(String fileName) throws IOException {
        byte[] buf = new byte[8192];
        try (InputStream is = Files.newInputStream(Paths.get(fileName))) {
            int len = is.read(buf);
            if (len < buf.length) {
                return Arrays.copyOf(buf, len);
            }
            ByteArrayOutputStream os = new ByteArrayOutputStream(16384);
            while (len != -1) {
                os.write(buf, 0, len);
                len = is.read(buf);
            }
            return os.toByteArray();
        }
    }

  

A seemingly small change that could reduce GC pauses if you do a lot of file I/O!

Oh and yeah, we're making this [change in Jenkins](https://github.com/jenkinsci/jenkins/pull/2816).
