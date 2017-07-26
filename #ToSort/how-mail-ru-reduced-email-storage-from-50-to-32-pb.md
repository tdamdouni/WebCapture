# How Mail.Ru Reduced Email Storage From 50 To 32 PB

_Captured: 2017-01-26 at 21:29 from [www.smashingmagazine.com](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)_

Meet the new [Sketch Handbook](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1), our brand **new Smashing book** that will help you master all the tricky, advanced facets of Sketch. Filled with **practical examples and tutorials in 12 chapters**, the book will help you become more proficient in your work. [Get the book now ->](https://shop.smashingmagazine.com/products/sketch-handbook?utm_source=magazine&utm_campaign=sketch-handbook&utm_medium=html-ad-content-1)

When the Russian ruble's exchange rate slumped two years ago, it drove us to think of cutting hardware and hosting costs for the Mail.Ru email service. To look at ways to save money, let's first **take a look at what email consists of**.

![Email content](https://www.smashingmagazine.com/wp-content/uploads/2017/01/01-preview-opt.png)[1](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Indexes and bodies account for only 15% of the storage size, whereas 85% is taken up by files. So, optimization of files (that is, attachments) is worth exploring in more detail. At the time, we didn't have file deduplication in place, but we estimated that it could shrink the total storage size by 36%, because many users receive the same messages, such as price lists from online stores and newsletters from social networks that contain [images](https://www.smashingmagazine.com/2013/12/imageoptim-cli-batch-compression-tool/) and so on. In this article, I'll describe how we implemented a deduplication system under the guidance of [PSIAlt](https://www.facebook.com/psialt).

We're dealing with a stream of files. When we receive a message, we must deliver it to the user as soon as possible. We need to be able to quickly recognize duplicates. An easy solution would be to name files based on their contents. We're using SHA-1 for this purpose. The initial name of the file is stored in the email itself, so we don't need to worry about it.

Once a new email arrives, we retrieve the files, compute their hashes and add the result to the email. It's a necessary step to be able to easily locate the files belonging to a particular email in our future storage when this email is being sent.

Now, let's upload a file to our storage and find out whether another file with the same hash already exists there. This means we'll need to store all hashes in memory. Let's call this storage for hashes "FileDB."

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/02-preview-opt.png)[8](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

A single file can be attached to different emails, so we'll need a counter that keeps track of all emails containing this file.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/03-preview-opt.png)[9](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

The counter increments with every new file uploaded. About 40% of all files are deleted, so if a user deletes an email containing files uploaded to the cloud, the counter must be decremented. If the counter reaches zero, the file can be deleted.

Here we face the first issue: Information about an email (indexes) is stored in one system, whereas information about a file is stored in another. This could lead to an error. For example, consider the following workflow:

  1. The system receives a request to delete an email.
  2. The system checks the email indexes.
  3. The system can see there's an attachment (SHA-1).
  4. The system sends a request to delete a file.
  5. A crash occurs, so the email doesn't get deleted.
![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/04-preview-opt.png)[10](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

In this case, the email stays in the system, but the counter gets decremented by 1. When the system receives a second request to delete this email, the counter gets decremented again -- and we could encounter a situation in which the file is still attached to an email but the counter is already at 0.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/05-preview-opt.png)[11](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Not losing data is critical. We can't have a situation in which a user opens an email and discovers no attachment there. That being said, storing some redundant files on disks is no big deal. All we need is a mechanism to unambiguously determine whether the counter is correctly set to 0. That's why we have one more field -- `magic`.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/06-preview-opt.png)[12](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

The algorithm is simple. Along with the hash of a file, we store a randomly generated number in an email. All requests to upload or delete a file take this random number into account: In case of an upload request, this number is added to the current value of the magic number; if it's a delete request, this random number is subtracted from the current value of the magic number.

Thus, if all emails have incremented and decremented the counter the correct number of times, then the magic number will also equal 0. Otherwise, the file must not be deleted.

Let's consider an example. We have a file named `sha1`. It's uploaded once, and the email generates a random (magic) number for it, which is equal to 345.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/07-preview-opt.png)[13](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Then a new email arrives with the same file. It generates its own magic number (123) and uploads the file. The new magic number is added to the current value of the magic number (345), and the counter gets incremented by 1. As a result, what we have in FileDB is the magic number with the value of 468 and the counter set to 2.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/08-preview-opt.png)[14](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

After the user deletes the second email, the magic number generated for this email is subtracted from the current value of the magic number (468), and the counter gets decremented by 1.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/09-preview-opt.png)[15](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Let's first look at the normal course of events. The user deletes the first email, and the magic number and the counter both become 0. This means the data is consistent and the file can be deleted.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/10-preview-opt-1.png)[16](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Now, suppose something goes wrong: The second email sends two delete requests. The counter being equal to 0 means there are no more links to the file, but the magic number, which equals 222, signals a problem: The file can't be deleted until the data is consistent.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/11-preview-opt-1.png)[17](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Let's develop the situation a little more. Suppose the first email also gets deleted. In this case, the magic number (-123) still signals an inconsistency.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/12-preview-opt-2.png)[18](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

As a safety measure, once the counter reaches 0 but the magic number doesn't (in our case, the magic number is 222 and the counter is 0), the file is assigned a "Do not delete" flag. This way, even if -- after a series of deletions and uploads -- both the magic number and the counter somehow become 0, we'll still know that this file is problematic and must not be deleted. The system isn't allowed to generate a magic peer 0. If you send 0 as the magic number, you'll receive an error.

Back to FileDB. Every entity has a set of flags. Whether you plan to use them or not, you're going to need them (if, say, a file needs to be marked as undeletable).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/13-preview-opt-2.png)[19](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

We have all of the file attributes, except for where the file is physically located. This place is identified by a server (IP) and a disk. There should be two such servers and two such disks. We store two copies of each file.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/14-preview-opt-2.png)[20](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

But one disk stores a lot of files (in our case, about 1 million), which means these records will be identified by the same disk pair in FileDB, so storing this information in FileDB would be wasteful. Let's put it in a separate table, PairDB, linked to FileDB via a disk pair ID.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/15-preview-opt-2.png)[21](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

I guess it goes without saying that, apart from a disk pair ID, we'll also need a `flags` field. I'll jump ahead a bit and mention that this field signals whether the disks are locked (say, one disk has crashed and the other is being copied, so no new data can be written to either of them).

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/16-preview-opt-2.png)[22](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Also, we need to know how much free space each disk has -- hence, the corresponding fields.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/17-preview-opt-2.png)[23](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

To make sure everything works fast, both FileDB and PairDB must be RAM-resident. We were using Tarantool 1.5, but now the latest version should be used. FileDB has five fields (20, 4, 4, 4 and 4 bytes long), which add up to 36 bytes. Also, each record has a 16-byte header, plus a 1-byte length pointer per field, which brings the total record size to 57 bytes.

Tarantool allows you to specify the minimum allocation size, so memory-associated overhead can be kept close to zero. We'll be allocating the exact amount of memory needed for one record. We have 12 billion files.

`(57 * 12 * 10^9) / (1024^3) = 637 GB`

But that's not all, we'll also need an index on the `sha1` field, which adds 12 more bytes to the total record size.

`(12 * 12 * 10^9) / (1024^3) = 179 GB`

All in all, 800 GB of RAM are needed. And let's not forget about replication, which doubles the amount of RAM required.

If we buy machines with 256 GB of RAM on board, we'd need eight of them.

We can assess the size of PairDB. The average file size is 1 MB and disk capacity is 1 TB, which allows storage of about 1 million files on a single disk; so, we'd need some 28,000 disks. One PairDB record describes two disks. Therefore, PairDB contains 14,000 records -- negligible compared to FileDB.

Now that we've got the database structure out of the way, let's turn to the API for interacting with the system. At first glance, we need the `upload` and `delete` methods. But don't forget about deduplication: Chances are good that the file we're trying to upload is already in storage, and uploading it a second time wouldn't make sense. So, the following methods are necessary:

  * `inc(sha1, magic)` increments the counter. If a file doesn't exist, it returns an error. Recall that we also need a magic number that helps to prevent incorrect file deletion.
  * `upload(sha1, magic)` should be called if `inc` has returned an error, which means this file doesn't exist and must be uploaded.
  * `dec(sha1, magic)` should be called if a user deletes an email. The counter is decremented first.
  * `GET /sha1` downloads a file via HTTP.

Let's take a closer look at what happens during uploading. For the daemon that implements this interface, we chose the IProto protocol. Daemons must scale well to any number of machines, so they don't store states. Suppose we receive a request via a socket:

The command name tells us the header's length, so we read the header first. Now, we need to know the length of the `origin-len` file. It's necessary to choose a couple of servers to upload it. We just retrieve all of the records (a few thousand) from PairDB and use the standard algorithm to find the needed pair: Take a segment with the length equal to the sum of free spaces on all pairs, randomly pick a point on this segment, and choose whatever pair this point belongs to.

However, choosing a pair this way is risky. Suppose all of our disks are 90% full -- and then we add a new empty disk. It's highly likely that all new files will be uploaded to this disk. To avoid this problem, we should sum not the free space of a disk pair, but the nth root of this free space.

So, we've chosen a pair, but our daemon is a streaming one, and if we start uploading a file to storage, there's no turning back. That being said, before uploading a real file, we'll upload a small test file first. If the test upload is successful, we'll read `filecontent` from the socket and upload it to storage; otherwise, another pair is chosen. SHA-1 hash can be read on the fly, so it is also checked during uploading.

Let's now examine a file upload from a loader to a chosen disk pair. On machines that contain the disks, we set up nginx and use the WebDAV protocol. An email arrives. FileDB doesn't have this file yet, so it needs to be uploaded to a disk pair via a loader.

But nothing prevents another user from receiving the same email -- suppose two recipients are specified. Remember that FileDB doesn't have this file yet, so one more loader will be uploading this very file and might pick the same disk pair for uploading.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/23-preview-opt.png)[29](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Nginx would likely resolve this situation correctly, but we need to control the whole process, so we'll save the file with a complex name.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/24-preview-opt-1.png)[30](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

The part of the name in red is where each loader puts a random number. Thus, the two `PUT` methods won't overlap and upload two different files. Once nginx responds with `201` (OK), the first loader performs an atomic `MOVE` operation, which specifies the final name of the file.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/25-preview-opt.png)[31](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

When the second loader is done uploading the file and also performs `MOVE`, the file will get overwritten, but it's no big deal because the file is one and the same. Once the file is on the disks, a new record needs to be added to FileDB. Our version of Tarantool is divided into two spaces. We've only been using `space0` so far.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/26-preview-opt.png)[32](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

However, instead of simply adding a new record to FileDB, we're using a stored procedure that either increments the file counter or adds a new record to FileDB. Why? In the time that has passed since the loader made sure the file doesn't exist in FileDB, uploaded it and proceeded to add a new record to FileDB, someone else could have uploaded this file and added the corresponding record. We've considered this very case: Two recipients are specified for one email, so two loaders start uploading the file; once the second loader finishes the upload, it also proceeds to add a new record to FileDB.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/27-preview-opt.png)[33](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

In this case, the second loader just increments the file counter.

Let's now look at the `dec` method. Our system has two high-priority tasks: to reliably write a file to disk and to quickly give it back to a client from this disk. Physically deleting a file generates a certain workload and slows down these two tasks. That's why we perform deletions offline. The `dec` method itself decrements the counter. If the latter becomes 0, just like the magic number, then it means nobody needs the file anymore, so we move the corresponding record from `space0` to `space1` in Tarantool.
    
    
    decrement (sha1, magic){
        counter--
        current_magic –= magic
    
        if (counter == 0 && current_magic == 0){
            move(sha1, space1)
        }
    }
    

Each storage has a Valkyrie daemon that monitors data integrity and consistency -- and it works with `space1`. There's one daemon instance per disk. The daemon iterates over all of the files on a disk and checks whether `space1` contains a record corresponding to a particular file, which would mean that this file should be deleted.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/28-preview-opt.png)[34](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

But after the `dec` method is called and a file is moved to `space1`, Valkyrie might take a while to find this file. This means that, in the time between these two events, the file may be reuploaded and, thus, moved to `space0` again.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/29-preview-opt.png)[35](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

That's why Valkyrie also checks whether a file exists in `space0`. If this is the case and the `pair_id` of the corresponding record points to a pair of disks that this Valkyrie instance is running on, then the record is deleted from `space1`.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/30-preview-opt.png)[36](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

If no record is found in `space0`, then the file is a potential candidate for deletion. However, between a request to `space0` and the physical deletion of a file, there's still a window of time in which a new record corresponding to this file might appear in `space0`. To deal with this, we put the file in quarantine.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/31-preview-opt.png)[37](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Instead of deleting the file, we append `deleted` and a timestamp to its name. This means we'll physically delete the file at `timestamp` plus some time specified in the config file. If a crash occurs and the file is deleted by mistake, the user will come to reclaim it. We'll be able to restore it and resolve the issue without losing any data.

Now, recall that there are two disks, with a Valkyrie instance running on each. The two instances are not synced. Hence the question: When should the record be deleted from `space1`?

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/32-preview-opt.png)[38](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

We'll do two things. First, for the file in question, let's make one of the Valkyrie instances the master. This is easily done by using the first bit of the file name: If it equals zero, then `disk0` is the master; otherwise, `disk1` is the master.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/33-preview-opt.png)[39](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

Let's introduce a processing delay. Recall that when a record sits in `space0`, it contains the `magic` field for checking consistency. When the record is moved to `space1`, this field is not used, so we'll put there a timestamp corresponding to the time that this record appeared in `space1`. This way, the master Valkyrie instance will start processing records in `space1` at once, whereas the slave will add some delay to the timestamp and will process and delete records from `space1` a little later.

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/34-preview-opt.png)[40](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

This approach has one more advantage. If a file was mistakenly put in quarantine on the master, it'll be evident from the log once we query the master. Meanwhile, the client that requested the file will fall back to the slave -- and the user will receive the needed file.

So, we have considered the situation in which the Valkyrie daemon locates a file named `sha1`, and this file (being a potential candidate for deletion) has a corresponding record in `space1`. What other variants are possible?

Suppose a file is on a disk, but FileDB doesn't have any corresponding record. If, in the case considered above, the master Valkyrie instance, for some reason, hasn't been working for some time, it would mean the slave's had enough time to put the file in quarantine and to delete the corresponding record from `space1`. In this case, we would also put the file in quarantine by using `sha1.deleted.timestamp`.

Another situation: A record exists but points to a different disk pair. This could happen during uploading if two recipients are specified for one email. Recall this scheme:

![](https://www.smashingmagazine.com/wp-content/uploads/2017/01/35-preview-opt.png)[41](https://www.smashingmagazine.com/2017/01/reducing-email-storage-mailru/)

What happens if the second loader uploads the file to a different pair than the first one? It will increment the counter in `space0`, but the disk pair where the file was uploaded would contain some junk files. What we need to do is make sure these files can be read and that they match `sha1`. If everything's fine, such files can be deleted at once.

Also, Valkyrie might encounter a file that has been put in quarantine. If the quarantine is over, this file will get deleted.

Now, imagine that Valkyrie encounters a good file. It needs to be read from disk, checked for integrity and compared to `sha1`. Then, Valkyrie needs to query the second disk to see if it has this same file. A simple `HEAD` method is enough here: The daemon running on the second disk will itself check the file's integrity. If the file is corrupt on the first disk, it's immediately copied over from the second disk. If the second disk doesn't have the file, its copy is uploaded from the first disk.

We're left with the last situation, which has to do with disk problems. If any problem with a disk is identified in the course of system monitoring, the problematic disk is put in service (read-only) mode, while on the second disk, the `UNMOVE` operation is run. This effectively distributes all of the files on the second disk among other disk pairs.

Let's get back to where we started. Our email storage used to look like this:

We've managed to reduce the total size by 18 PB after implementing the new system:

Emails now occupy 32 PB (25% for indexes, 75% for files). Thanks to the 18-PB cut, we didn't have to buy new hardware for quite some time.

As of now, there are no known examples of SHA-1 collisions. There exist collision examples for its internal compression function (SHA-1 freestart collision), though. Given 12 billion files, the probability of a hash collision is less than 10^-38.

But let's assume it's possible. In this case, when a file is requested by its hash value, we check whether it has the correct size and CRC32 checksum that were saved in the indexes of the corresponding email during upload. That is to say, the requested file will be provided if and only if it was uploaded along with this email.

_(vf, yk, il, al)_
