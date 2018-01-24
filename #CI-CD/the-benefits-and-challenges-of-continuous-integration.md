# The Benefits and Challenges of Continuous Integration

_Captured: 2017-10-24 at 20:24 from [dzone.com](https://dzone.com/articles/the-benefits-and-the-drawbacks-of-continuous-integ?edition=334723&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-10-24)_

The Nexus Suite is uniquely architected for a DevOps native world and creates value early in the development pipeline, provides precise contextual controls at every phase, and accelerates DevOps innovation with automation you can trust. [Read how in this ebook](https://dzone.com/go?i=222229&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Without a doubt, continuous integration (CI) has become a mainstream principle for software development. The benefits of CI are well-known across the industry and it would be hard to find anyone who would argue against implementing it.

Here, I wanted to gather those benefits into one central place. But I also thought it would be fun to play devil's advocate and try to find the drawbacks, or challenges, of continuous integration.

## **What Is Continuous Integration?**

Fundamentally, continuous integration (CI) is a development practice where developers integrate code into a shared repository serval times a day. In that repository, the code is verified by an automated build that detects any problems early in the process. This allows teams to spend less time backtracking and more time building new features.

## **The Benefits of Continuous Integration**

### **1\. Risk Mitigation**

According to [Martin Fowler,](https://martinfowler.com/articles/continuousIntegration.html) the most substantial benefit of continuous integration is reduced risks. By deferring code integration, teams increasingly compound the number and severity of their merge conflicts. When teams integrate frequently (with an automated build), they reduce the number of potential risks because they always know the current state of their system.

### **2\. Quality Insurance**

Teams that implement continuous integration have greater confidence in their operations. They know the automated build is catching defects immediately, which allows them to promise quality. They aren't guessing the number of bugs in their system either, which allows them to give accurate numbers to their teammates and a better service for their customers.

### **3\. Increased Visibility and Enhanced Teamwork**

An automated build provides a team complete visibility into their system. They know the number of issues and can combat them quickly. Increased visibility also allows teams to coordinate before a small issue turns into something bigger.

## **The Challenges of Continuous Integration**

### **1\. Organizational Culture Changes**

Some businesses prefer traditional methodologies and might have a hard time implementing continuous integration. They would have to retrain staff members, which would mean overhauling existing operations. Managers may be resistant because continuous integration doesn't help them meet their immediate company objectives (e.g. money over quality).

### **2\. Difficult to Maintain**

Building an automated code repository is not a simple task. Teams must build the proper testing suite and spend time writing test cases versus developing code. At first, this could slow them down and make them lose faith in completing their own projects on time. If the testing suite isn't stable, it could work perfectly on some days, but other days it may not work. The team would then have to spend more time trying to figure out what happened.

### **3\. Numerous Error Messages**

For larger development teams, they may see CI error messages daily and start ignoring them all together because they have other tasks and concerns. They may start to see a broken build as a normal thing and defects could start accumulating on top of each other.

The DevOps Zone is brought to you in partnership with Sonatype Nexus. See how the Nexus platform infuses precise open source component intelligence into the DevOps pipeline early, everywhere, and at scale. [Read how in this ebook](https://dzone.com/go?i=222230&u=https%3A%2F%2Fwww.sonatype.com%2Faccelerate-devops-early-everywhere-at-scale-ebook%3Futm_campaign%3Ddzone%26utm_source%3Dearly%2520everywhere%2520ebook).

Opinions expressed by DZone contributors are their own.
