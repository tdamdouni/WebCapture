# A RESTful Way to Find and Retrieve Data

_Captured: 2018-01-24 at 22:20 from [dzone.com](https://dzone.com/articles/a-restful-way-to-find-and-retrieve-data?edition=357095&utm_source=Weekly%20Digest&utm_medium=email&utm_campaign=Weekly%20Digest%202018-01-24)_

In a recent blog post, we discussed _[creating_ web services](https://www.knime.com/blog/creating-restful-services-with-knime-an-update) using [KNIME Analytics Platform](https://www.knime.com/knime-analytics-platform) and [KNIME Server](https://www.knime.com/knime-server). Now, we want to look at _[calling_ web services with KNIME](https://www.knime.com/blog/knime-and-rest-a-dream-team-for-life-sciences-discovery-informatics).

Since this post is from the Life Sciences team at KNIME and we've been investigating [ChEMBL web services](https://www.ebi.ac.uk/chembl/ws) recently, we'd like to use them as an example here. Please note that there is a set of [community KNIME nodes](https://www.knime.com/book/embl-ebi-nodes-for-knime-trusted-extension) for accessing ChEMBL and ChEBI, and we are intentionally duplicating some of that functionality here.

[ChEMBL](https://www.ebi.ac.uk/chembl/) itself is a great open data resource. It provides a large collection of linked information on compounds and their structures, biological targets and their sequences, and biological assays and their experimental details. The data are largely collected from scientific publications with each entry in the database represented by a unique identifier: a ChEMBL ID. It's all freely available for download in relational form or can be accessed using a REST API. That's what we look at here.

Don't stop reading if you're from another field and not really interested in ChEMBL or the data it contains! The patterns we use here for interacting with the web services and looking at the results will work for many other RESTful web APIs.

## Calling One Single REST Service

When we first sat down to try out the ChEMBL services, we started with a very simple four-node workflow:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure1.png?itok=wkoTqQCs)

> _Figure 1: Simple generic workflow to call REST-based web services._

This table shows the URLs we're fetching. They retrieve data about the compounds with the unique identifiers CHEMBL ID as CHEMBL25 (aspirin) and CHEMBL1201320 (esomeprazole), respectively.

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure2.png?itok=9TtLiSUc)

> _Figure 2: The two URLs we want to fetch._

Configuring the GET Request node is almost embarrassingly easy:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure3.png?itok=I_9y7BY3)

> _Figure 3: Configuration of the RESTful web service call._

We've asked the web service to return JSON, so the next node is a JSON to Table node. We configure this to extract all of the elements in the nested JSON objects returned by the ChEMBL service:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure4.png?itok=cmn3Z7Ow)

> _Figure 4: Configuration of the JSON to Table node._

Finally, we can look at the results. Here's part of the table showing the two compounds we wanted: aspirin and esomeprazole.

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure5.png?itok=y5FA6wsq)

> _Figure 5: Table showing part of the two rows returned by the web service._

## Orchestrating a Cascade of REST Services

This simple workflow enables us to fetch the information contained in ChEMBL about a couple of molecules. This was easy to put together and is quite useful, but there are things we can do to make it even better. Have a look at this:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure6.png?itok=La6Ugulu)

> _Figure 6: A complete workflow allowing us to enter a list of ChEMBL IDs and retrieve details about some of them._

We start by making it possible to provide a list of ChEMBL IDs.

  * We use the ChEMBL look-up service to figure out if they exist and, if so, what type of entity they correspond to.
  * The third node is interactive and, through a UI, allows us to pick the type of entity we want more information about.
  * Based on the previous type choice, the set of nodes inside the CASE Switch performs the appropriate web service calls, while output parsing moves the results into a KNIME table for further processing.
  * The metanodes and wrapped metanodes encapsulate a lot of complexity and, in the case of the wrapped metanodes, allow us to combine a number of interactive views into one composite view (more information about this can be found in the [KNIME TV](https://www.youtube.com/user/KNIMETV) video [Data Viz With KNIME](https://youtu.be/ea20YWaqOXw)).

Not only can we take advantage of this interactivity in [KNIME Analytics Platform](https://www.knime.com/knime-analytics-platform), we can also use it in the [WebPortal](https://www.knime.com/nodeguide/enterprise/webportal) by deploying the workflow to the [KNIME Server](https://www.knime.com/knime-server). This functionality allows our workflow to be used as a web application by people who may not want to use KNIME Analytics Platform (such people actually do exist!) or who may not currently have the Analytics Platform installed.

Although we show what it looks like to use this workflow via the WebPortal below, you can also check out the views we show in KNIME Analytics Platform itself. Right-click the wrapped metanodes and select **Interactive View**.

### Step 1: Retrieving the List of Molecules via ChEMBL IDs

We start with a prompt for the set of ChEMBL IDs we want to look up:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure7.png?itok=xdhbt6Pt)

> _Figure 7: The first page of the ChEMBL look-up application. Here we provide (paste in) a set of ChEMBL IDs._

These IDs are then passed to the ChEMBL look-up service, which returns the type of each entity it finds along with the URL that can be used to look up details about it. We display these results using a pair of linked tables. The first allows us to select an entity type and the second shows the entities of the types that were found:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure8.png?itok=vFhcMgj0)

_Figure 8: The second page of the ChEMBL look-up application. This allows us to select the entity type we are interested in and pick the individual rows we want more information about._

### Step 2. Retrieving the Details for the Selected Molecules

After selecting the entity type we want to work with and de-selecting any rows we are not interested in, we click the **Next** button (not shown in the screenshot). The output of calling the ChEMBL details web services with those rows is displayed in the next page, shown here for a few compounds:

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure9.png?itok=5xhZskTk)

_Figure 9: Results of molecule details call. Here we can browse the available structural information as well as pick the entries for a next web service call._

Now, we've got the structural information that ChEMBL stores for the compounds we looked up. This is nice by itself if we're just interested in chemistry, but we often also want to see the bioactivity data that can be found in ChEMBL. The next part of the workflow takes care of this.

We pick several compounds for which we would like to retrieve the bioactivities (let it be CHEMBL10 and CHEMBL102740) and click the **Next** button. After a few seconds, the following page with two linked tables comes up. Only a few rows and columns of the second table are displayed here.

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure10.png?itok=KH1q79cb)

> _Figure 10: Final page of the workflow with bioactivity information for selected entries._

This page allows us to explore which types of bioactivities were found using the first table. Selecting one of the bioactivity types in the first table will show the matching entries in the second table. The second table provides extensive information on each bioactivity point such as assay, compound, target, and publication details. This Bioactivity call could be performed for Assays and Targets as well. For this example, we are extracting up to 1,000 bioactivity data points per entry; to retrieve all of the available data points, we could incorporate the Bioactivity GET Request node (it's hiding inside the ChEMBL Bioactivity Metanode) in a loop using one of our example workflows ([looping over chunks of the data](https://www.knime.com/nodeguide/control-structures/loops/looping-over-chunks-of-the-data)).

### Step 3: Similarity Search Across Molecules

Some of you might be quite familiar with the full functionality of ChEMBL nodes, which allow similarity and substructure searches for compounds based on their SMILES representation. We felt our REST example would be lacking if we didn't try that out, too. So, here it comes.

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure11.png?itok=jcUnXUpA)

> _Figure 11: A workflow searching for similar compounds within ChEMBLdb._

The workflow starts by asking us to provide SMILES strings for the search and to select Search Type (Similarity or Substructure) and Similarity threshold (used only for the Similarity Search Type).

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure12.png?itok=2dBfcUMO)

> _Figure 12: The first page of the ChEMBL Structure Search workflow._

Next, the results of structure search are displayed in two tables: Successful queries (shown below) and Failed queries.

![](https://files.knime.com/sites/default/files/styles/inline_large/public/a_restful_way_to_find_and_retrieve_data_-_figure13.png?itok=2n-czZDZ)

> _Figure 13: The second page of the ChEMBL Structure Search workflow displays the results of structure search._

At this point, we can pick entries (or select all retrieved compounds) and continue exploring the data available for these compounds in the latest ChEMBL release via Molecule Details and Bioactivity nodes, which are described in the first workflow.

As a final touch in the web service workflows, we added the option to download the results of the searches as comma-separated files. To do this, select the results and proceed to the next page in the Web portal.

![](https://files.knime.com/sites/default/files/styles/inline_small/public/a_restful_way_to_find_and_retrieve_data_-_figure14.png?itok=ZHuQ1TGY)

_Figure 14: Final page of ChEMBL Structure Search workflow. Clicking the hyperlink downloads the search results from the server._

## Wrapping Up

In this post, we started with a quick workflow for accessing ChEMBL web services from within KNIME Analytics platform. We then expanded that workflow and showed how to add some interactive views to make it usable as a web application with the KNIME WebPortal. This is really just a starting point; we could do a lot more with ChEMBL web services from within KNIME and this could be revisited in a future blog post! In the meantime, however, we hope we've managed to spark your interest and find the workflows themselves useful.
