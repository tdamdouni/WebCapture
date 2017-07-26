# Remembering Clean Architecture

_Captured: 2017-05-20 at 09:59 from [dzone.com](https://dzone.com/articles/remembering-clean-architecture?edition=299091&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-05-19)_

The single app analytics solutions to [take your web and mobile apps to the next level.](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D322361301%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Try today! Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208121&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143155%3Bdc_trk_aid%3D321036346%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

As developers, we can spend considerable periods of time debating and advocating various languages and frameworks.

Irrespective of the pros and cons of a particular language or framework, if the architecture isn't clear and agreed upon from the beginning, then interest in building new and the ability to maintain existing functionality diminishes.

Basically, the pride that went into creating it wanes, and what was once fun to work on is now a burden.

Does the loose structure of **Fig.1** below seem familiar?

It led me to ask the following questions:

What is the intent of this application? How is that intent fulfilled? Why are there so many packages at the root level?

![Image title](https://dzone.com/storage/temp/5322577-fig1.png)

_Fig. 1_

The answers to the above can certainly be found, but it comes across that things were added after the fact without really knowing where they are meant to go.

This seems like a case where the architecture wasn't clear from the beginning and, as the application grew, it became further unclear.

There is no clear separation between what the application does and how it does it.

## Begin With a Clean Architecture

Before even selecting which language or framework to use, determine and agree upon the architecture.

Robert C. Martin and others have provided great material on this subject, and I am going to share my understanding.

Before I even started refactoring the code, I first decided upon the architecture (see Fig. 2 below).

![Image title](https://dzone.com/storage/temp/5322578-fig2.png)

_Fig. 2_

See this example repository on [GitHub ](https://github.com/mahanhz/clean-architecture-example)for the intent of each module.

## Refactor to a Cleaner Architecture

### Core

![Image title](https://dzone.com/storage/temp/5322586-fig3.png)

The** usecase** implements the interfaces in the **boundary.enter** package and uses the ones in **boundary.exit**.

**Depends on:** This module has no dependency on any other module. It is also framework agnostic.

### Periphery

#### Data

This module contains the repositories that retrieve or edit data in the database.

It implements the interfaces defined in the **boundary.exit** package, meaning that this module has a direct dependency on core.

**Depends on: **core

#### Web

This module contains the controllers (e.g. REST API).

This module uses the adapter module to communicate with the core, meaning that it has no direct dependency on the core.

**Depends on: **adapter

### Adapter

![Image title](https://dzone.com/storage/temp/5322600-fig4.png)

My original intention of the **adapter **was to handle all the communication with the core, hence nothing in the periphery would ever depend directly on the core.

However as described above, the **data **module in the periphery does not use the adapter, it's only used by the **web **module (converts the domain objects into the **api **that the web module expects).

The reason is that I didn't want any framework knowledge inside the adapter module, and since I am using Spring Data in my data module, there isn't a way to use the data module without making the adapter Spring Data aware.

**Depends on: **core

### Configuration

![Image title](https://dzone.com/storage/temp/5322608-fig5.png)

This module glues everything together.

It contains the MainApplication (in this case a Spring Boot application), all the Spring @Configuration files and the resources needed to make the application work.

**Depends on: **adapter, core, data, and web

### Other Improvements

During the refactoring, I detected that some of the tests were actually integration tests and that they no longer had a home inside any of these new modules.

As a result, I moved all these tests to a new **integration-test** module.

## Summary

Although there is no definitive answer on how to architect a software solution, I feel that agreeing upon a clean architecture up front will pay dividends.

Above I have described my journey towards a cleaner architecture and, as an aid, I have created a sample application on [GitHub ](https://github.com/mahanhz/clean-architecture-example)to demonstrate it.

CA App Experience Analytics, a whole new level of visibility. [Learn more.](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D) Brought to you in partnership with [CA Technologies](https://dzone.com/go?i=208122&u=https%3A%2F%2Fad.doubleclick.net%2Fddm%2Ftrackclk%2FN6040.130331DZONE%2FB11232955.150143157%3Bdc_trk_aid%3D322361143%3Bdc_trk_cid%3D81513735%3Bdc_lat%3D%3Bdc_rdid%3D%3Btag_for_child_directed_treatment%3D).

Opinions expressed by DZone contributors are their own.
