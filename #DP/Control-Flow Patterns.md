# Control-Flow Patterns

_Captured: 2015-08-30 at 19:50 from [www.workflowpatterns.com](http://www.workflowpatterns.com/patterns/control/index.php)_

### Downloads of the original and revised control-flow patterns papers:

N. Russell, A.H.M. ter Hofstede, W.M.P. van der Aalst, and N. Mulyar.   
[ **Workflow Control-Flow Patterns: A Revised View**](http://www.workflowpatterns.com/patterns/control/../../documentation/documents/BPM-06-22.pdf). (PDF, 1.04Mb) _  
BPM Center Report BPM-06-22 _, BPMcenter.org, 2006.

W.M.P van der Aalst, A.H.M. ter Hofstede, B. Kiepuszewski, and A.P. Barros. **  
[Workflow Patterns](http://www.workflowpatterns.com/patterns/control/../../documentation/documents/wfs-pat-2002.pdf).** (PDF, 718 Kb).

## Introduction

The _Workflow Patterns Initiative_ was established with the aim of delineating the fundamental requirements that arise during business process modelling on a recurring basis and describe them in an imperative way. The first deliverable of this research project was a set of twenty patterns describing the control-flow perspective of workflow systems. Since their release, these patterns have been widely used by practitioners, vendors and academics alike in the selection, design and development of workflow systems [[vdAtHKB03](http://www.workflowpatterns.com/patterns/control/bibliography.php)]. This body of work presents the first systematic review of the original twenty control-flow patterns and provides a formal description of each of them in the form of a Coloured Petri-Net (CPN) model. It also identifies twenty three new patterns relevant to the control-flow perspective. Detailed context conditions and evaluation criteria are presented for each pattern and their implementation is assessed in fourteen commercial offerings including workflow and case handling systems, business process modelling formalisms and business process execution languages.

## Revisiting the Original Patterns 

Here we present a revised description of the original twenty control-flow patterns previously presented in [[vdAtHKB03](http://www.workflowpatterns.com/patterns/control/bibliography.php)]. Although this material is motivated by earlier research conducted as part of the _Workflow Patterns Initiative_, the descriptions for each of these patterns have been thoroughly revised and a new set of evaluations have been undertaken. In several cases, detailed review of a pattern has indicated that there are potentially several distinct ways in which the original pattern could be interpreted and implemented. In order to resolve these ambiguities, we have taken the decision to base the revised definition of the original pattern on the _most restrictive_ interpretation of its operation and to delineate this from other possible interpretations that could be made. In several situations, a substantive case exists for consideration of these alterative operational scenarios and where this applies, these are presented in the form of new control-flow patterns.

## New Control Flow Patterns

Review of the patterns associated with the control-flow perspective over the past few years has led to the recognition that there are a number of distinct modelling constructs that can be identified during process modelling that are not adequately captured by the original set of twenty patterns. Here we present twenty three new control-flow patterns that augment the existing range of patterns described above and elsewhere [[vdABtHK00](http://www.workflowpatterns.com/patterns/control/bibliography.php), [vdAtHKB03](http://www.workflowpatterns.com/patterns/control/bibliography.php)]. In an attempt to describe the operational characteristics of each pattern more rigourously, we also present a formal model in Coloured Petri-Net (CPN) format for each of them. In fact the explicit modelling of the original patterns using CPN Tools helped identify a number of new patterns as well as delineating situations where some of the original patterns turned out to be collections of patterns.

## Basic Control Flow Patterns

This class of pattern captures elementary aspects of process control and are similar to the definitions of these concepts initially proposed by the Workflow Management Coalition (WfMC) [[Wor99](http://www.workflowpatterns.com/patterns/control/bibliography.php)].

## Advanced Branching and Synchronization Patterns

Here we present a series of patterns which characterise more complex branching and merging concepts which arise in business processes. Although relatively commonplace in practice, these patterns are often not directly supported or even able to be represented in many commercial offerings. The original control-flow patterns identified four of these patterns: _Multi-Choice, Synchronizing Merge, Multi-Merge and Discriminator. _

In this revision, the _Multi-Choice _and _Multi-Merge _have been retained in their previous form albeit with a more formal description of their operational semantics. For the other patterns however, it has been recognized that there are a number of distinct alternatives to the manner in which they can operate. The original _Synchronizing Merge_ now provides the basis for three patterns: the _Structured Synchronizing Merge _(WCP7), the _Acyclic Synchronizing Merge _(WCP37) and the _General Synchronizing Merge _(WCP38).

In a similar vein, the original _Discriminator _pattern is divided into six (6) distinct patterns: the _Structured Discriminator _(WCP9), the _Blocking Discriminator _(WCP28), the _Cancelling Discriminator _(WCP29), the _Structured Partial Join _(WCP30), the _Blocking Partial Join _(WCP31) and the _Cancelling Partial Join _(WCP32). One other addition has been the _Generalized AND-Join (_WCP33) which identifies a more flexible AND-join useful in concurrent processes.

Of these patterns, the original descriptions for the _Synchronizing Merge_ and the _Discriminator _are superseded by their structured definitions.

6\. [Multi-Choice  
](http://www.workflowpatterns.com/patterns/control/advanced_branching/wcp6.php)7\. [Structured Synchronizing Merge  
](http://www.workflowpatterns.com/patterns/control/advanced_branching/wcp7.php)8\. [Multi-Merge  
](http://www.workflowpatterns.com/patterns/control/advanced_branching/wcp8.php)9\. [Structured Discriminator  
](http://www.workflowpatterns.com/patterns/control/advanced_branching/wcp9.php)28\. [Blocking Discriminator  
](http://www.workflowpatterns.com/patterns/control/new/wcp28.php)29\. [Cancelling Discriminator  
](http://www.workflowpatterns.com/patterns/control/new/wcp29.php)30\. [Structured Partial Join  
](http://www.workflowpatterns.com/patterns/control/new/wcp30.php)31\. [Blocking Partial Join  
](http://www.workflowpatterns.com/patterns/control/new/wcp31.php)32\. [Cancelling Partial Join  
](http://www.workflowpatterns.com/patterns/control/new/wcp32.php)33\. [Generalised AND-Join  
](http://www.workflowpatterns.com/patterns/control/new/wcp33.php)37\. [Local Synchronizing Merge  
](http://www.workflowpatterns.com/patterns/control/new/wcp37.php)38\. [General Synchronizing Merge  
](http://www.workflowpatterns.com/patterns/control/new/wcp38.php)41\. [Thread Merge  
](http://www.workflowpatterns.com/patterns/control/new/wcp41.php)42\. [Thread Split ](http://www.workflowpatterns.com/patterns/control/new/wcp42.php)

## Multiple Instance Patterns

Multiple instance patterns describe situations where there are multiple threads of execution active in a process model which relate to the same activity (an hence share the same implementation definition). Multiple instances can arise in three situations:

  1. An activity is able to initiate multiple instances of itself when triggered (we denote this form of activity a _multiple instance _activity);
  2. A given activity is initiated multiple times as a consequence of it receiving several independent triggerings (e.g. as part of a loop or in a process instance in which there are several concurrent threads of execution as might result from a _Multi-Merge _for example; and 
  3. Two or more activities in a process share the same implementation definition. This may be the same activity definition in the case of a multiple instance activity or a common sub-process definition in the case of a block activity. Two (or more) of these activities are triggered such that their executions overlap (either partially or wholly).

Although all of these situations potentially involve multiple concurrent instances of an activity or sub-process, it is the first of them in which we are most interested as they require the triggering and synchonization of multiple concurrent activity instances. This group of patterns focusses on the various ways in which these events can occur.

Similar to the differentiation introduced in the Advanced Branching and Synchronization Patterns to capture the distinction between the _Discriminator _and the _Partial Join _pattern variants, three new patterns have been introduced to recognize alternative operational semantics for multiple instances. These are the the _Static Partial Join for Multiple Instances _(WCP34), the _Cancelling Static Partial Join for Multiple Instances _(WCP35) and the _Dynamic Partial Join for Multiple Instances _(WCP36).

12\. [Multiple Instances without Synchronization  
](http://www.workflowpatterns.com/patterns/control/multiple_instance/wcp12.php)13\. [Multiple Instances with a Priori Design-Time Knowledge  
](http://www.workflowpatterns.com/patterns/control/multiple_instance/wcp13.php)14\. [Multiple Instances with a Priori Run-Time Knowledge  
](http://www.workflowpatterns.com/patterns/control/multiple_instance/wcp14.php)15\. [Multiple Instances without a Priori Run-Time Knowledge  
](http://www.workflowpatterns.com/patterns/control/multiple_instance/wcp15.php)34\. [Static Partial Join for Multiple Instances  
](http://www.workflowpatterns.com/patterns/control/new/wcp34.php)35\. [Cancelling Partial Join for Multiple Instances  
](http://www.workflowpatterns.com/patterns/control/new/wcp35.php)36\. [Dynamic Partial Join for Multiple Instances](http://www.workflowpatterns.com/patterns/control/new/wcp36.php)

## State-based Patterns

State-based patterns reflect situations for which solutions are most easily accomplished in process languages that support the notion of state. In this context, we consider the state of a process instance to include the broad collection of data associated with current execution including the status of various activities as well as process-relevant working data such as activity and case data elements.

The original patterns include three patterns in which the current state is the main determinant in the course of action that will be taken from a control-flow perspective. These are: _Deferred Choice _(WCP16), where the decision about which branch to take is based on interaction with the operating environment, _Interleaved Parallel Routing _(WCP 17), where two or more sequences of activities are undertaken on an interleaved basis such that only one activity instance is executing at any given time and _Milestone _(WCP18), where the enabling of a given activity only occurs where the process is in a specific state.

In recognition of further state-based modelling scenarios, four new patterns have also been identified. These are: _Critical Section _(WCP39), which provides the ability to prevent concurrent execution of specific parts of a process, _Interleaved Routing _(WCP40), which denotes situations where a group of activities can be executed sequentially in _any _order, and _Thread Merge _(WCP41) and _Thread Split _(WCP42) which provide for coalescence and divergence of distinct threads of control along a single branch.

## Cancellation and Force Completion Patterns

Several of the patterns above (e.g. (WCP6) _Structured Synchronizing Merge _and (WCP9) _Structured Discriminator_) have variants that utlize the concept of activity cancellation where enabled or active activity instance are withdrawn. Various forms of exception handling in processes are also based on cancellation concepts. This section presents two cancellation patterns - _Cancel Task _(WCP19) and _Cancel Case _(WCP20).

Three new cancellation patterns have also been identified _Cancel Region _(WCP25), _Cancel Multiple Instance Activity _(WCP26) and _Complete Multiple Instance Activity _(WCP27).

## Iteration Patterns 

The following patterns deal with capturing repetitive behaviour in a workflow.

## Termination Patterns 

The following patterns deal with the circumstances under which a workflow is considered to be completed.

11\. [Implicit Termination  
](http://www.workflowpatterns.com/patterns/control/structural/wcp11.php)43\. [Explicit Termination ](http://www.workflowpatterns.com/patterns/control/new/wcp43.php)

## Trigger Patterns 

The following patterns deal with the external signals that may be required to start certain tasks.

23\. [Transient Trigger  
](http://www.workflowpatterns.com/patterns/control/new/wcp23.php)24\. [Persistent Trigger](http://www.workflowpatterns.com/patterns/control/new/wcp24.php)

## Disclaimer

We, the authors and the associated institutions, assume no legal liability or responsibility for the accuracy and completeness of any product-specific information contained in this body of work. All possible efforts have been make to ensure that the results presented are, to the best of our knowledge, up to date and correct.
