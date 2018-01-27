# Continuous Testing Principles for Cross Browser Testing and Mobile Apps

_Captured: 2018-01-25 at 15:39 from [dzone.com](https://dzone.com/articles/continuous-testing-principles-for-cross-browser-te?edition=355136&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=mobile%202018-01-25)_

Majority of organizations are already deep into Agile practices with a goal to be DevOps and continuous delivery (CD) compliant.

While some may say that maximum % of test automation would bring these organizations toward DevOps, It takes more than just test automation.

To mature DevOps practices, a continuous testing approach needs to be in place, and it is more than automating functional and non-functional testing. Test automation is obviously a key enabler to be agile, release software faster and address market events, however, continuous testing (CT) requires some additional considerations.

**[Tricentis](https://www.tricentis.com/what-is-continuous-testing/) defines CT accordingly:**

" _CT is the process of executing automated tests as part of the software delivery pipeline in order to obtain feedback on the business risks associated with a software release candidate as rapidly as possible. It evolves and extends test automation to address the increased complexity and pace of modern application development and delivery_ "

![](https://ek121268.files.wordpress.com/2018/01/devops-cycle-extended.png?w=820&h=406)

The above suggests that a CT process would include a high degree of test automation, with a risk-based approach and a fast feedback loop back to developer upon each product iteration.

## How to Implement CT

  * A **risk-based approach** means sufficient [coverage](https://info.perfectomobile.com/factors-magazine.html) of the right platforms (Browsers and Mobile devices) - such platform coverage eliminates business risks and assures high user-experience. Such platform coverage is continuous maintenance requirements as the market changes.
  * Continuous Testing needs an automated **end-to-end testing** that integrates existing development processes while excluding errors and enabling continuity throughout SDLC. That principle can be broken accordingly: 
    * **Implement the "right" tests** and shift them into the build process, to be executed upon each code commit. Only reliable, stable, and high-value tests would qualify to enter this CT test bucket.
    * Assure the **CT test bucket runs within only 1 CI** -> In CT, there is no room for multiple CI channels.
    * **Leverage [reporting](https://www.perfectomobile.com/solutions/test-automation-analysis/perfecto%E2%80%99s-digitalzoom%E2%84%A2-reporting) and analytics dashboards** to reach "smart" testing decisions and actionable feedback, that support a continuous testing workflow. As the product matures, tests need maintenance, and some may be retired and replaced with newer ones.
  * **Stable Lab and test environment** is a key to ongoing CT processes. The lab should be at the heart of your CT, and should support the above platform coverage requirements, as well as the CT test suite with the test frameworks that were used to develop these tests.
  * Utilize if possible **artificial intelligence** (AI) and** machine learning** (ML)/deep-learning (DL) solutions to better optimize your CT test suite and shorten the overall release activities.
![](https://ek121268.files.wordpress.com/2018/01/coveragecube.png?w=820&h=526)

Lastly, for a **CT** practice to work time after time, the above principles needs to be **continuously optimized, maintained, and adjusted** as things change either within the product roadmap or in the market.

**Happy CT!**

![](https://dz2cdn1.dzone.com/storage/rc-covers/7391100-dzone-aicover.jpg)
