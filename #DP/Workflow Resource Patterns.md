# Workflow Resource Patterns

_Captured: 2015-08-30 at 19:49 from [www.workflowpatterns.com](http://www.workflowpatterns.com/patterns/resource/index.php)_

### Download of the resource patterns paper: 

N. Russell, A.H.M. ter Hofstede, D. Edmond, and W.M.P. van der Aalst.  
**[Workflow Resource Patterns](http://www.workflowpatterns.com/patterns/resource/../../documentation/documents/Resource%20Patterns%20BETA%20TR.pdf).** (PDF, 418 Kb).  
BETA Working Paper Series, WP 127, Eindhoven University of Technology, Eindhoven, 2004.

## Introduction

Workflow systems seek to provide an implementation vehicle for complex, recurring business processes. Notwithstanding this common objective, there are a variety of distinct features offered by commercial workflow management systems. These differences result in significant variations in the ability of distinct tools to represent and implement the plethora of requirements that may arise in contemporary business processes. Many of these requirements recur quite frequently during the requirements analysis activity for workflow systems and abstractions of these requirements serve as a useful means of identifying the key components of workflow languages. Previous work has identified a number of Workflow Control-flow Patterns and Workflow Data Patterns, which characterize the range of control flow and data constructs that might be encountered when modelling and analysing workflows. In this body of work, we describe a series of Workflow Resource Patterns that aim to capture the various ways in which resources are represented and utilized in workflows. By delineating these Patterns in a form that is independent of specific workflow technologies and modelling languages, we are able to provide a comprehensive treatment of the resource perspective and we subsequently use these Patterns as the basis for a detailed comparison of a number of commercially available workflow management systems and business process modelling languages.

Before you view the different resource patterns, you may wish to examine one of the following options to gain a better understanding of the work presented to you:

  * For a general explanation of terms, go to the [resource modelling](http://www.workflowpatterns.com/patterns/resource/resource_modelling.php) web page. 
  * For an introduction to the concepts used in this body of work, go to the [workflow structure](http://www.workflowpatterns.com/patterns/resource/workflow_structure.php) web page. 
  * To read about the lifecycle of a work item, go to the [work distribution of resources](http://www.workflowpatterns.com/patterns/resource/work_distribution.php) web page. 

## Creation Patterns 

Creation Patterns correspond to limitations on the manner in which a work item may be executed. They are specified at design time, usually in relation to a task, and serve to restrict the range of resources that can undertake work items that correspond to the task. They also influence the manner in which a work item can be matched with a resource that is capable of undertaking it.

The essential rationale for creation patterns is that they provide a degree of clarity about how a work item should be handled after creation during the offering and allocation stages prior to it being executed. This ensures that the operation of a process conforms with its intended design principles and operates as efficiently and deterministically as possible.

In terms of the work item lifecycle, creation patterns come into effect at the time a work item is created. This state transition occurs at the beginning of the work item lifetime and is illustrated by the bold arrow in Figure [3](http://www.workflowpatterns.com/patterns/resource/index.php). For all of these patterns it is assumed that there is an associated organizational model which allows resources to be uniquely identified and that there is a mechanism to distribute work items to specific resources identified in the organizational model. As creation patterns are specified at design time, they usually form part of the process model which describes a business process.

![Figure 3: Creation Patterns](http://www.workflowpatterns.com/patterns/resource/images/fig3.png)

> _Figure 3 : Creation Patterns_

  1. [Direct Distribution](http://www.workflowpatterns.com/patterns/resource/creation/wrp1.php)
  2. [Role-Based Distribution](http://www.workflowpatterns.com/patterns/resource/creation/wrp2.php)
  3. [Deferred Distribution ](http://www.workflowpatterns.com/patterns/resource/creation/wrp3.php)
  4. [Authorization ](http://www.workflowpatterns.com/patterns/resource/creation/wrp4.php)
  5. [Separation of Duties ](http://www.workflowpatterns.com/patterns/resource/creation/wrp5.php)
  6. [Case Handling ](http://www.workflowpatterns.com/patterns/resource/creation/wrp6.php)
  7. [Retain Familiar ](http://www.workflowpatterns.com/patterns/resource/creation/wrp7.php)
  8. [Capability-Based Distribution](http://www.workflowpatterns.com/patterns/resource/creation/wrp8.php)
  9. [History-Based Distribution](http://www.workflowpatterns.com/patterns/resource/creation/wrp9.php)
  10. [Organisational Distribution ](http://www.workflowpatterns.com/patterns/resource/creation/wrp10.php)
  11. [Automatic Execution ](http://www.workflowpatterns.com/patterns/resource/creation/wrp11.php)

## Push Patterns 

Push Patterns characterise situations where newly created work items are proactively offered or allocated to resources by the system. These may occur indirectly by advertising work items to selected resources via a shared work list or directly with work items being allocated to specific resources. In both situations however, it is the system that takes the initiative and causes the distribution process to occur. Figure [4](http://www.workflowpatterns.com/patterns/resource/index.php) illustrates (as bold arcs) the potential state transitions associated with push-based distribution:

  * S:offer_s corresponds to a work item being offered to a single resource
  * S:offer_m corresponds to a work item being offered to multiple resources (one of which will ultimately execute it)
  * S:allocate corresponds to a work item being directly allocated to a resource immediately after it has been created
![Figure 4: Push Patterns](http://www.workflowpatterns.com/patterns/resource/images/fig4.png)

> _Figure 4: Push Patterns_

**Figure 4:** Push Patterns

Nine push Patterns have been identified. These divide into three distinct groups. The first three Patterns identify the actual manner of work distribution - whether the workflow system offers the work item to a single resource, to multiple resources or whether it allocates it directly to a single resource (footnote [1).](http://www.workflowpatterns.com/patterns/resource/footnotes.php) These patterns correspond directly to the bold arcs in Figure [4](http://www.workflowpatterns.com/patterns/resource/index.php).

The second group of patterns relate to the means by which a resource is selected to undertake a work item where there are multiple possible resources identified. Three possible strategies are described - random allocation, round robin allocation and shortest queue. These patterns correspond to alternate ways in which the S:offer_s and S:allocate transitions may occur.

The final three patterns identify the timing of the distribution process and in particular the relationship between the availability of a work item for offering/allocation to resources and the time at which it commences execution. Three variants are possible - work items are offered/allocated before they have commenced (early distribution), after they have commence (late distribution) or the two events are simultaneous (distribution on enablement). These Patterns do not have a direct analogue in Figure [4](http://www.workflowpatterns.com/patterns/resource/index.php) but relate to the time at which the S:offer_s, S:offer_m and S:allocate transitions may occur with respect to the work item's readiness to be executed (i.e. already started, immediate start or subsequent start).

## Pull Patterns 

Pull Patterns correspond to the situation where individual resources are made aware of specific work items, that require execution, either via a direct offer from the system or indirectly through a shared work list. The commitment to undertake a specific task is initiated by the resource itself rather than the system. Generally this results in the work item being placed on the specific work list for the individual resource for later execution although in some cases, the resource may elect to commence execution on the work item immediately. The various state transitions associated with pull patterns are illustrated in Figure [5](http://www.workflowpatterns.com/patterns/resource/index.php):

  * R:allocate_s corresponds to the situation where a work item has been offered to a single resource and the resource has indicated it will commit to executing at some future time
  * R:allocate_m corresponds to the situation where a work item has been offered to multiple resources and one of the resources has indicated it will commit to executing at some future time. The work item is deemed to be allocated to that resource and is no longer available to the other resources to which it was offered
  * R:start_s corresponds to the situation where a work item which has been offered to a single resource being started by that resource
  * R:start_m corresponds to the situation where a work item which has been offered to multiple resources is started by one of those resources
  * R:start corresponds to the situation where a work item which has been allocated to a single resource being started by that resource.

Six pull patterns have been identified. These divide into two distinct groups. The first three patterns identify the specifics of the actual "pull" action initiated by the resource, with a particular focus on the work item state before and after the interaction. These patterns correspond to the bold arcs in Figure [5](http://www.workflowpatterns.com/patterns/resource/index.php). The second group of patterns focus on the sequence in which the work items are presented to the resource and the ability of the system and the individual resource to influence the sequence and manner in which they are displayed. The final pattern in this group illustrates the degree of freedom that the resource has in selecting the next work item to execute. These patterns do not have a direct analogue in Figure [5](http://www.workflowpatterns.com/patterns/resource/index.php) but apply to all of the "pull" transitions illustrated as bold arcs.

![Figure 5: Pull Patterns](http://www.workflowpatterns.com/patterns/resource/images/fig5.png)

> _Figure 5: Pull Patterns_

**Figure 5:** Pull Patterns

Note that the distinction between push and pull patterns is identified by the initiator of the various transitions. For the push patterns in Figure [4](http://www.workflowpatterns.com/patterns/resource/index.php), the state transitions for work items are all triggered by the system, whereas in Figure [5](http://www.workflowpatterns.com/patterns/resource/index.php) which denotes pull patterns, the transitions are initiated by individual resources. Other characteristics of interest which ultimately lead to additional pull patterns, relate to whether the resource has the ability to reorder their own work sequence or it is determined by the system, and whether a resource can select which work item they wish to commence next from those on its work queue.

## Detour Patterns 

Detour Patterns refer to situations where work item distributions that have been made for resources are interrupted either by the system or at the instigation of the resource. As a consequence of this event, the normal sequence of state transitions for a work item is varied. The range of possible scenarios for detour patterns are illustrated in Figure [6](http://www.workflowpatterns.com/patterns/resource/index.php).

![Figure 6: Detour Patterns](http://www.workflowpatterns.com/patterns/resource/images/fig6.png)

> _Figure 6: Detour Patterns_

There are a number of possible impacts on a work item, depending on its current state of progression and whether the detour was initiated by the resource with which the work item was associated or by the system. These include:

  * _delegation_ \- where a resource allocates a work item previous allocated to it to another resource
  * _escalation_ \- where the system attempts to progress a work item that has stalled by offering or allocating it to another resource
  * _deallocation_ \- where a resource makes a previously allocated or started work item available for offer and subsequent allocation
  * _ stateful reallocation_ \- where a resource allocates a work item that it has started to another resource and the current state of the work item is retained
  * _stateless reallocation_ \- where a resource allocates a work item that it has started to another resource but the current state is not retained (i.e. the work item is restarted) 
  * _suspension/resumption_ \- where a resource temporarily suspends execution of a work item or recommences execution of a previously suspended work item
  * _skipping_ \- where a resource elects to skip the execution of a work item allocated to it
  * _redo_ \- where a resource repeats execution of a work item completed earlier
  * _pre-do_ \- where a resource executes a work item that is ahead of the current execution point in a case

Each of these actions relate to one or more transitions in Figure [6](http://www.workflowpatterns.com/patterns/resource/index.php) and corresponds to a specific patterns below.

## Auto-Start Patterns 

Auto-start patterns relate to situations where execution of work items is triggered by specific events in the lifecycle of the work item or the related process definition. Such events may include the creation or allocation of the work item, completion of another instance of the same work item or a work item that immediately precedes the one in question. The state transitions associated with these patterns are illustrated by bold arcs in Figure [7](http://www.workflowpatterns.com/patterns/resource/index.php).

![Figure 7: Auto-start Patterns](http://www.workflowpatterns.com/patterns/resource/images/fig7.png)

> _Figure 7: Auto-start Patterns_

**Figure 7:** Auto-start Patterns

## Visibility Patterns 

Visibility Patterns classify the various scopes in which work item availability and commitment are able to be viewed by resources. They give a indication of how open to scrutiny the operation of a PAIS is.

## Multiple Resource Patterns 

Up to this point, the focus of this catalogue of patterns has been on situations where there is a one-to-one correspondence between the resources and work items in a given allocation or execution. In other words, resources cannot work on different work items simultaneously and it is not possible that multiple resources work on the same work item. In situations where people are not restricted by information technology, there is often a many-to-many correspondence between the resources and work items in a given allocation or execution. Therefore, it may be desirable to support this using process technology. Here we discuss patterns relaxing the one-to-one correspondence between resources and work items that we have assumed previously.

Let us first consider the one-to-many situation, i.e., resources _can_ work on different work items simultaneously. This is a fairly simple requirement, supported by most systems.

_Simultaneous Execution_ is easy to support and contemporary systems support this one-to-many correspondence between the resources and work items in a given allocation or execution. Unfortunately, it is more difficult to support a many-to-one correspondence, i.e., multiple resources working on the same work item. This is a pity since for more complicated activities people tend to work in teams and collaborate to jointly executed work items. Moveover, there is also a lack of consideration for work items that require access to multiple non-human resources (e.g. plant and equipment, fuel, consumables etc.) in order to proceed. Given the limited support of today's PAIS, only one pattern is proposed which implies a many-to-one correspondence.

## Disclaimer 

We, the authors and the associated institutions, assume no legal liability or responsibility for the accuracy and completeness of any product-specific information contained in this body of work. All reasonable efforts have been make to ensure that the results presented are, to the best of our knowledge, up to date and correct.
