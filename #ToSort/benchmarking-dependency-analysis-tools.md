# Benchmarking Dependency Analysis Tools

_Captured: 2017-12-22 at 15:34 from [dzone.com](https://dzone.com/articles/benchmarking-dependency-analysis-tools?edition=347102&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=performance%202017-12-22)_

[OWASP Top 10 2017](https://www.owasp.org/images/7/72/OWASP_Top_10-2017_%28en%29.pdf.pdf) lists A9: "using components with known vulnerabilities" as a major security issue facing companies. The recent Equifax data breach was actually caused by a known security issue in the Apache Struts library; it was an instance of the OWASP A9. There are several vendors in the market with products that claim to address this problem. However, it is often very difficult to compare and contrast the results from the tools that do dependency analysis. We recently released an open-source [Evaluation Framework for Dependency Analysis (EFDA)](https://github.com/continuous-security/efda) to help address this challenge.

![](https://res.cloudinary.com/peerlyst/image/upload/c_limit,h_274,w_600/v1/post-attachments/Screen_Shot_2017-12-02_at_10.02.01_AM_c0pdhb)

EFDA provides a set of test cases and scoring criteria to benchmark dependency analysis. It currently covers 8 different languages across 17 package managers and has 38 different test scenarios. The idea is that you run the tool based on the tests and then compare the results with the expected results. For each passing test you get a point that contributes towards the total. You can also customise and configure the importance of a given test by giving it a weight. There is a public [EFDA Spreadsheet](https://docs.google.com/spreadsheets/d/1rAmOxEQDw1SpKetbrGOqNU5YmfnRh_aFqrizU8D2MKk) that allows you to compute the total score.

The full details of the framework and the thoughts behind the design are given [here](https://www.sourceclear.com/blog/Evaluation-Framework-for-Dependency-Analysis/). We welcome everyone to contribute to the [project](https://github.com/continuous-security/efda) by suggesting more tests or benchmarking and publishing the results of dependency analysis tools.
