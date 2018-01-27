# Navigating AUTOSAR models with complex queries

_Captured: 2018-01-03 at 16:23 from [blogs.itemis.com](https://blogs.itemis.com/en/navigating-autosar-model-with-complex-queries?utm_source=hs_email&utm_medium=email&utm_content=59754756&_hsenc=p2ANqtz--tYRmRnArsY2sr83H6rWwTIdudlvNeW1vdPh14W_1fgcEsIz2oEzdGULrPecfdvcLY8Id84VGqlFAzteTK4K4onICZzw&_hsmi=59754756)_

In the [previous blog posts](https://blogs.itemis.com/en/how-to-configure-your-free-autosar-model-viewer) I showed you how the basic features of Eclipse and Artop can be used to perform basic [searches and navigation on AUTOSAR models](https://blogs.itemis.com/en/search-in-and-navigate-through-autosar-models). However, there are also often cases, where a user wants to perform more complex queries on AUTOSAR models.

E.g. we might want to find PDUs with specific characteristis (number of signals, certain ID range). In the example for this blog post, we want to find all SenderReceiverInterfaces in our model, that actually don't have any data element.

![Labyrinth-Complex-find-a-way.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Labyrinth-Complex-find-a-way.jpg?t=1514992779618&width=2172&height=1035&name=Labyrinth-Complex-find-a-way.jpg)

##   
Sphinx Workflows

With Sphinx we can create complex scripts in a running Artop, written in Java or (even better) in Xtend. Xtend in especially suited for the job, since it has nice concepts for complex model queries. The required steps are:

  * Create an Eclipse "Plugin"-Project. The plugin-project provides the mechanism for Java/Xtend compilation and the setup of all the required dependencies.
  * Implement the query
  * Create a "Run configuration" and execute the query.

## Creating the code

To execute dynamic code from the workspace, Sphinx will look for implementations of WorkspaceWorkflow classes in the project, so we need a small implementation:
    
    
    public class Query extends  WorkspaceWorkflow {  
    new() {  
             children += new QueryComponent  
    }  
    }

The actual action happens in the Query component:
    
    
    class QueryComponent extends AbstractModelWorkflowComponent {  
      
    override protected invokeInternal(WorkflowContext arg0, ProgressMonitor arg1, Issues arg2) {  
             val m = arg0.get(IModelWorkflowSlots.MODEL_SLOT_NAME) as List<EObject>  
      
             val c = m.get(0).eResource.resourceSet.allContents.filter(SenderReceiverInterface).  
                 filter[it.dataElements.empty].toList  
      
             showResults(c)  
    }  
      
    }

The code for this example is actually very simple:

  * The workflow framework will invoke the _invokeInternal_ method of all components in sequence.
  * Arguments to the workflow are passed in so-called "slots". The framework passes the elements that are selected in the Eclipse explorer in the slot with the name _IModelWorkflowSlots.MODEL_SLOT_NAME_
  * The next line contains our example query. For simplicity, we just use the ResourceSet of the selected object and filter the entire model for _SenderReceiverInterface_ elements. The next filter statement looks for _SenderReceiverInterfaces_ that have no data elements. A list is constructed out of that.
  * At this point, we could print the list of results to the console. However, since this is a full IDE, we would like to use the search view that Eclipse uses itself for search queries and which allows us to do further navigations. The code for that is in a dedicated method:
    
    
    def protected showResults(Collection<? extends EObject> coll) {  
      
    Display.^default.syncExec([  
    NewSearchUI.activateSearchResultView();  
                 val view =  NewSearchUI.getSearchResultView();  
    ])  
      
             val query = new ModelSearchQuery(null) {  
    override getResultLabel(int nMatches) {  
    "Script query"  
    }  
    };  
      
             val searchResult = new ModelSearchResult(query);  
             coll.forEach[searchResult.addMatch(new ModelSearchMatch(it))]  
      
    Display.^default.syncExec([  
    (NewSearchUI.getSearchResultView() as SearchView).showSearchResult(searchResult)  
    ])  
    }

Using run configurations to run the queries

A workflow can be run either through the context menu of a element in the model explorer or through Eclipse run configurations. The context menu approach however does not support passing of arguments through an UI. So we will be using run configurations, even if we do not use workflow parameters right now (that will be shown in a later blog post). So we create a new "Sphinx workflow" and set the path to our Workflow class:

![Eclipse-sphinx.jpg](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Eclipse-sphinx.jpg?t=1514992779618&width=2172&height=1530&name=Eclipse-sphinx.jpg)

If we click the "Run" button, we will get the results in the search window. In our case, we are using the "Blueprint" model that is provided with Artop / AUTOSAR and find the following interfaces that have no data elements:

![Interface.png](https://blogs.itemis.com/hs-fs/hubfs/Blog/Software%20Development/Interface.png?t=1514992779618&width=960&name=Interface.png)

## Summary

In the short series of three blog posts, we have shown how Eclipse and Artop can be used to configure a powerful tool for examining AUTOSAR models at no cost. In addition to the normal navigations and model searches, you can interactively use any Java-based language to write custom model queries - we recommend Xtend because of its powerful language features that support model navigation. The example above is quite simple, but it is very easy to write much more powerful queries.

In addition, you can use any Java-based libraries and frameworks to help you do the job. In a customer setting, we need to group PDUs according to various criteria and we make use of the JGraphT library.
