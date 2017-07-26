# Querying Content in Crafter CMS

_Captured: 2017-03-28 at 20:47 from [dzone.com](https://dzone.com/articles/querying-content-in-crafter-cms?edition=286932&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=dd%202017-03-28)_

## Types of Content Queries

Crafter CMS supports 3 specific types of content queries:

  * **Cross-content Lucene/Solr queries**. This enables you to query any/all content objects, by any group of properties.
  * **Filtered Structural Queries**. This enables you to query against the repository structure, e.g. "Get all articles by author XYZ."
  * **Content Item specific query**. This enables you to write queries inside of a given content item.

### Type 1: Make a Lucene/Solr Query

The following code examples use the Crafter Search Service in Crafter Engine to get content. You can find the interface for this service [HERE](https://github.com/craftercms/engine/blob/2.5.xhttps://github.com/craftercms/search/blob/2.5.x/crafter-search-api/src/main/java/org/craftercms/search/service/SearchService.java).
    
    
    def queryStatement = 'content-type:"/component/article" AND author:"Russ Danner"'
    
    def query = searchService.createQuery()
    query = query.setQuery(queryStatement)
    
    def executedQuery = searchService.search(query)
    def itemsFound = executedQuery.response.numFound
    def items = executedQuery.response.documents
    
    return items

### Type 2: Make a Query for Content Based on Structure

The following code examples use the Site Item Service in Crafter Engine to get content. You can find the interface for this service [HERE](https://github.com/craftercms/engine/blob/2.5.x/src/main/java/org/craftercms/engine/service/SiteItemService.java).
    
    
    def topNavItems = [:]
    def siteDir = siteItemService.getSiteTree("/site/website", 2)
    
    if(siteDir) {
        def dirs = siteDir.childItems
        dirs.each { dir ->
                def dirName = dir.getStoreName()
                def dirItem = siteItemService.getSiteItem("/site/website/${dirName}/index.xml")
                if (dirItem != null) {
                    def dirDisplayName = dirItem.queryValue('internal-name')
                       topNavItems.put(dirName, dirDisplayName)
                }
       }
    }
    
    return topNavItems

#### Make a Query for Content Based on Structure With Filter

The following code examples use the Site Item Service in Crafter Engine to get content. In the example, we build on the Site Item Service of getting objects under a specific tree in the repository by supplying a filter that will be applied to each object first to determine if it should be part of the result. Filters can make their determination based on the path or the content or even "outside" influence.

  * You can find the interface for this service [HERE](https://github.com/craftercms/engine/blob/2.5.x/src/main/java/org/craftercms/engine/service/SiteItemService.java).
  * Note in the example below we define our own filter based on the ItemFilter interface found [HERE](https://github.com/craftercms/core/blob/2.5.x/src/main/java/org/craftercms/core/service/ItemFilter.java).
  * However, you may use out of the box filters as well if they meet your needs. These are found [HERE](https://github.com/craftercms/engine/tree/2.5.x/src/main/java/org/craftercms/engine/service/filter).
  * Finally be aware that for simple filename patterns, methods for this already exist in the Site Item Service and no filter is required (but they make for an easy to understand example).
    
    
    import org.craftercms.core.service.ItemFilter
    import org.craftercms.core.service.Item
    import java.util.List
    
    
    def result = [:]
    def navItems = [:]
    def siteDir = siteItemService.getSiteTree("/site/website", 2, new StartsWithAItemFilter(), null)
    
    if(siteDir) {
        def dirs = siteDir.childItems
        dirs.each { dir ->
                def dirName = dir.getStoreName()
                def dirItem = siteItemService.getSiteItem("/site/website/${dirName}/index.xml")
                if (dirItem != null) {
                    def dirDisplayName = dirItem.queryValue('internal-name')
                       navItems.put(dirName, dirDisplayName)
                }
       }
    }
    result.navItems = navItems
    
    return result
    
    
    /**
     * Define a filter that returns only items that have a name that starts with "A" or "a"
     */
    class StartsWithAItemFilter implements ItemFilter {
    
        public boolean runBeforeProcessing() {
            return true
        }
    
        public boolean runAfterProcessing() {
            return false
        }
    
        public boolean accepts(Item item, List acceptedItems, List rejectedItems, boolean runBeforeProcessing) {
    
          if (item.getName().toLowerCase().startsWith("a")) {
              return true
          }
    
          return false
        }
     }

### Type 3: Make a Query Against Fields in a Content Object

The following code examples use the Site Item Service in Crafter Engine to get content. You can find the interface for this service [HERE](https://github.com/craftercms/engine/blob/2.5.x/src/main/java/org/craftercms/engine/service/SiteItemService.java).
    
    
    def result = [:]
    def segment = "a segment value" // could come from profile, query param etc
    
    // load a specific content object
    def itemDom = siteItemService.getSiteItem("/site/components/sliders/default.xml")
    
    // query specific values from the object
    result.header = itemDom.queryValue("/component/targetedSlide//segment[contains(.,'" +  segment + "')]../label")
    result.image = itemDom.queryValue("/component/targetedSlide//segment[contains(.,'" +  segment + "')]/../image")
    
    return result
