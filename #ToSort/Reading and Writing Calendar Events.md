# Reading and Writing Calendar Events

_Captured: 2016-03-15 at 00:26 from [developer.apple.com](https://developer.apple.com/library/ios/documentation/DataManagement/Conceptual/EventKitProgGuide/ReadingAndWritingEvents.html#//apple_ref/doc/uid/TP40004775-SW1)_

## Connecting to the Event Store

On iOS 5 and later, initialize an `[EKEventStore](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` object with the default initializer:
    
    
    EKEventStore *store = [[EKEventStore alloc] init];

On iOS 6 and later, you must request access to use the user's Calendar database with the `[requestAccessToEntityType:completion:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method after the event store is initialized. Requesting access to an entity type asynchronously prompts the user to allow or deny your app from using their calendar information. You should handle cases for when the user grants and denies access to your app:
    
    
    [store requestAccessToEntityType:EKEntityTypeEvent completion:^(BOOL granted, NSError *error) {
    
    
        // handle access here
    
    
    }];

On OS X, initialize an `EKEventStore` object with the designated initializer `initWithAccessToEntityTypes:`:
    
    
    EKEventStore *store = [[EKEventStore alloc] initWithAccessToEntityTypes:EKEntityMaskEvent];

You do not need to request access to use the user's Calendar database on OS X, because access is automatically granted.

An `EKEventStore` object requires a relatively large amount of time to initialize and release. Consequently, you should not initialize and release a separate event store for each event-related task. Instead, initialize a single event store when your app loads, and use it repeatedly to ensure that your connection is long-lived.

An event store instance must not be released before other Event Kit objects; otherwise, undefined behavior may occur.

## Retrieving Events

There are two ways to retrieve events. Fetching via predicates, or search query, will return zero or more events that match a given query. Fetching via unique identifiers will return a single event that corresponds to the given identifier.

**Note:** Retrieving events from the Calendar database does not necessarily return events in chronological order. To sort an array of `EKEvent` objects by date, call `[sortedArrayUsingSelector:](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/Foundation/Classes/NSArray_Class/index.html)` on the array, providing the selector for the `[compareStartDateWithEvent:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` method.

### Using Predicates

It's common to fetch events that fall within a date range. The `EKEventStore` method `[eventsMatchingPredicate:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` fetches all events that fall within the date range specified in the predicate you provide. Listing 1-1 demonstrates how to fetch all events that occur between one day before and one year after the current date.

**Listing 1-1** Fetching events with a predicate
    
    
    // Get the appropriate calendar
    
    
    NSCalendar *calendar = [NSCalendar currentCalendar];
    
    
    // Create the start date components
    
    
    NSDateComponents *oneDayAgoComponents = [[NSDateComponents alloc] init];
    
    
    oneDayAgoComponents.day = -1;
    
    
    NSDate *oneDayAgo = [calendar dateByAddingComponents:oneDayAgoComponents
    
    
                                                  toDate:[NSDate date]
    
    
                                                 options:0];
    
    
    // Create the end date components
    
    
    NSDateComponents *oneYearFromNowComponents = [[NSDateComponents alloc] init];
    
    
    oneYearFromNowComponents.year = 1;
    
    
    NSDate *oneYearFromNow = [calendar dateByAddingComponents:oneYearFromNowComponents
    
    
                                                       toDate:[NSDate date]
    
    
                                                      options:0];
    
    
    // Create the predicate from the event store's instance method
    
    
    NSPredicate *predicate = [store predicateForEventsWithStartDate:oneDayAgo
    
    
                                                            endDate:oneYearFromNow
    
    
                                                          calendars:nil];
    
    
    // Fetch all events that match the predicate
    
    
    NSArray *events = [store eventsMatchingPredicate:predicate];

You can specify a subset of calendars to search by passing an array of `[EKCalendar](https://developer.apple.com/library/ios/documentation/DataManagement/Reference/EKCalendarClassRef/index.html)` objects as the _calendars_ parameter of the `[predicateForEventsWithStartDate:endDate:calendars:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method. You can get the user's calendars from the event store's `[calendarsForEntityType:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method. Passing `nil` tells the method to fetch from all of the user's calendars.

Because the `[eventsMatchingPredicate:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method is synchronous, you may not want to run it on your app's main thread. For asynchronous behavior, run the method on another thread with the `dispatch_async` function or with an `[NSOperation](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/NSOperation_class/index.html)` object.

### Using Unique Identifiers

If you know the event's unique identifier because you fetched it previously with a predicate, you can use the `EKEventStore` method `[eventWithIdentifier:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` to fetch the event. If it is a recurring event, this method will return the first occurrence of the event. You can get an event's unique identifier with the `[eventIdentifier](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` property.

## Creating and Editing Events

**Note:** If you're developing on iOS, you have the option of letting users modify event data with the event view controllers provided in the Event Kit UI framework. For information on how to use these event view controllers, see [Providing Interfaces for Events](https://developer.apple.com/library/ios/documentation/DataManagement/Conceptual/EventKitProgGuide/UsingEventViewControllers.html).

Create a new event with the `[eventWithEventStore:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` method of the `[EKEvent](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` class.

You can edit the details of a new event or an event you previously fetched from the Calendar database by setting the event's corresponding properties. Some of the details you can edit include:

  * The event's start and end dates with the `[startDate](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` and `[endDate](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventClassRef/index.html)` properties

  * The calendar with which the event is associated with the `[calendar](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKCalendarItemClassRef/index.html)` property

  * The alarms associated with the event with the `[alarms](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKCalendarItemClassRef/index.html)` property (see [Configuring Alarms](https://developer.apple.com/library/ios/documentation/DataManagement/Conceptual/EventKitProgGuide/ConfiguringAlarms/ConfiguringAlarms.html) for more details)

  * The event's recurrence rule, if it is a repeating event, with the `[recurrenceRules](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKCalendarItemClassRef/index.html)` property (see [Creating Recurring Events](https://developer.apple.com/library/ios/documentation/DataManagement/Conceptual/EventKitProgGuide/CreatingRecurringEvents/CreatingRecurringEvents.html) for more details)

## Saving and Removing Events

**Important:** If your app modifies a user's Calendar database, _it must get confirmation from the user before doing so_. An app should never modify the Calendar database without specific instruction from the user.

Changes you make to an event are not permanent until you save them. Save your changes to the Calendar database with the `EKEventStore` method `[saveEvent:span:commit:error:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)`. If you want to remove an event from the Calendar database, use the `EKEventStore` method `[removeEvent:span:commit:error:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)`. Whether you are saving or removing an event, implementing the respective method automatically syncs your changes with the calendar the event belongs to (CalDAV, Exchange, and so on).

If you are saving a recurring event, your changes can apply to all future occurrences of the event by specifying `[EKSpanFutureEvents](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` for the _span_ parameter of the `saveEvent:span:commit:error:` method. Likewise, you can remove all future occurrences of an event by specifying `[EKSpanFutureEvents](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` for the _span_ parameter of the `[removeEvent:span:commit:error:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method.

**Note:** If you pass `[NO](https://developer.apple.com/library/ios/documentation/Cocoa/Reference/ObjCRuntimeRef/index.html)` to the _commit_ parameter, make sure that you later invoke the `[commit:](https://developer.apple.com/library/ios/documentation/EventKit/Reference/EKEventStoreClassRef/index.html)` method to permanently save your changes.
