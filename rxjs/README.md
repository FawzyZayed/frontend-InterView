
1 - Observable,
2 - Subscription
3 -Pipe
4 - of
5 - map
6 - PLUCK
7 - filter
8 - first
9 - Difference between combineLatest, zip, withLatestFrom?
10 - switchMap/mergeMap/ConcatMap/exhaustMap
11 - takeUntil
12 - TAP
13 - debounceTime, distinctUntilChanged:
14 - catchError
15 - throttleTime(3000):
16 - What is RxJS ?
17 - What is Obserable?
18 - What is the difference between an observable and a promise?
19 - What is the difference between Cold and Hot Observables ?
20 - What are RxJS Operators ?
21 - What is Observers and Subscriptions ?
22 - What is Subject?
23 - What is the difference between subject, behaviorSubject, replaySubject, asyncSubject?
24 - What is Reactive programming and how does it relate to Angular?
25 - higher-order Observable?
26 - Schedulers?
27 - What is the difference between Reactive Programming and Imperative Programming?
28 - What do you understand by the term Non-Blocking in RxJS?
29 - What does Asynchronous means in the context of RxJS or Reactive programming?
30 - What is the difference between Failure and Error?
31 - What is the difference between Imperative, Functional and Reactive Programming?



## 1 - Observable
a function that returns a stream of values

## 2 - Subscription
represents the execution of an Observable by calling the method “.subscribe”.

Most frequently used operators :-

## 3 - Pipe:
the way to use operators, returns another Observable

## 4 - of:
emitting values in a sequence.

## 5 - map:
transform an Observable of items into another Observable 

## 6 - PLUCK:
Similar to map but Pluck is used when we just need to pass single field value
```sh
const data = [{id:1, value:'one'}, {id:2, value:'two'}, {id:3, value:'three'}];
const obsPluck$ = from(data).pipe(
  pluck('value')
).subscribe(x => console.log(x));
```
## 7 - filter:
filter the values from source Observable 

## 8 - first:
if we are only interested in the first value that meets the Observable needs.
Use case: the sing up page of an app

## 9 - Difference between combineLatest, zip, withLatestFrom?
combineLatest:
combines multiple Observables to create an Observable whose values are calculated from the latest values of each of its input Observables
Use case: real-time text filters

Zip:
will wait for all observable to emit and then it zips those values into an array as an output.

withLatestFrom:
```sh
//emit every 5s
const source = interval(5000);
//emit every 1s
const secondSource = interval(1000);
//withLatestFrom slower than source
const example = secondSource.pipe(
  //both sources must emit at least 1 value (5s) before emitting
  withLatestFrom(source),
  map(([first, second]) => {
    return `Source (1s): ${first} Latest From (5s): ${second}`;
  })
);
```
/*
  "Source (1s): 4 Latest From (5s): 0"
  "Source (1s): 5 Latest From (5s): 0"
  "Source (1s): 6 Latest From (5s): 0"
  ...
*/

## 10 - switchMap/mergeMap/ConcatMap:
merged Observables in the output Observable, emitting values only from the most recently projected Observable
Use case: product detail page
```sh
ngOnInit(): void {
    this.route.paramMap
      .pipe(
        switchMap((paramMap: ParamMap)
          => this.productService.getProduct(+paramMap.get('id')))
      ).subscribe(...);
  }
 ```
switchMap cancels previous HTTP requests that are still in progress, while mergeMap lets them finish
ConcatMap Strategy —Queuing up every new Observable, and subscribing to a new observable only when the last observable completed

Mapping: 
- flatMap/mergeMap - creates an Observable immediately for any source item, all previous Observables are kept alive
- concatMap - waits for the previous Observable to complete before creating the next one
- switchMap - for any source item, completes the previous Observable and immediately creates the next one
- exhaustMap - source items are ignored while the previous Observable is not completed

## 11 - takeUntil:
takeUntil subscribes and begins mirroring the source Observable. It also monitors a second Observable, notifier that you provide. If the notifier emits a value, the output Observable stops mirroring the source Observable and completes. If the notifier doesn’t emit any value and completes then takeUntil will pass all values
Use case: managing unsubscriptions in Angular components

## 12 - TAP:
used to perform transparent actions such as logging.

## 13 - debounceTime, distinctUntilChanged:
These two operators are commonly used together,  debounceTime(1000) will make observable to wait for 1 sec before it can emit users input and distinctUntilChanged will only output distinct values, based on the last emitted value
```sh
obs$.pipe(
map(event => event.target.value),
debounceTime(1000),
distinctUntilChanged())
.subscribe((value) => console.log(value));
```
## 14 - catchError:
returning observable with error messages

## 15 - throttleTime(3000):
the subscription will only receive values after the time.

## 16 - What is RxJS ?
RxJS uses JavaScript reactive programming. it makes writing asynchronous code simple

## 17 - What is Stream ?
A stream refers to values of data overtime

## 18 - What is Obserable?
is an object that over time and asynchronously emits multiple data values

## 19 - What is the difference between an observable and a promise?
Promise: 
- emits a single value, 
- is Not Lazy A Promise cannot be cancelled
Observable: 
- emits multiple values over a time.
- is cold. It's not called until we're registered to it.
- You may cancel an Observable with the unsubscribe() method
- Observable provides a lot of efficient operators 

## 20 - What is the difference between Cold and Hot Observables ?
- Cold observables start to run in up and subscription, so observable sequence only starts pushing values to observers when subscribe is called.
- hot observables produce values even before subscriptions made.such as (mousemove events, WebSocket connections)

## 21 - What are RxJS Operators ?
a method that acts on an Observable and changes the stream in some way

## 22 - What is Observers and Subscriptions ?

- Observer is a set of callbacks that know how to listen to the values of the Observable.

- Subscription is an observable execution

## 23 - What is Subject?
Subject is a special type of Observable that allows values to be multicasted to many Observers
Every Subject is an Observer. It is an object with the methods next(v), error(e), and complete().

## 24 - What is the difference between subject, behaviorSubject, replaySubject, asyncSubject?
- Subject: only upcoming values
- behaviorSubject: one previous value and upcoming values
- replySubject all previous value and upcoming values
- asyncSubject latest value when stream will close

## 25 - What is Reactive programming and how does it relate to Angular?
- The principle of responsive programming is that you can just build the different streams and operations that take place on those flows
- Angular uses RxJS for some aspects of its internal service, such as Http, Router, etc.
RxJS is a very powerful library that facilitates the design of applications.

## 26 - higher-order Observable?
is an Observable that emits other Observables.

## 27 - Schedulers?
A scheduler controls the execution of when the subscription has to start and be notified.
Rx.Observable.of(42).repeat().subscribe()

## 28 - What is the difference between Reactive Programming and Imperative Programming?
- Reactive programming is a declarative programming paradigm which deals with asynchronous data streams.
- In Reactive Programming, observables emit data, and send it to the subscribers. This process can be called as data being PUSHed in reactive programming. 
- On the other hand, data is being PULLed in imperative programming, where we explicitly request data (requesting data from the DB.. etc)

## 29 - What do you understand by the term Non-Blocking in RxJS?
This concept is used in an API that allows access to the resource if available; otherwise, it immediately returns informing the caller that the resource is not currently available or the operation has been initiated and not yet completed.

## 30 - What does Asynchronous means in the context of RxJS or Reactive programming?
Asynchronous is the antonym of synchronous processing, which implies that the client only resumes its execution once the service has processed the request.

## 31 - What is the difference between Failure and Error?
- A failure can be defined as an unexpected event within a service that prevents it from functioning normally.
-  An error is a common condition that can appear during input validation that will be communicated to the client as part of the message's normal processing.

## 32 - What is the difference between Imperative, Functional and Reactive Programming?
- Imperative Programming: Imperative programming is a programming paradigm where each line of code is sequentially executed to produce the desired result. This programming paradigm forces programmers to write "how" a program will solve a certain task.

- Functional Programming: Functional programming is a programming paradigm where we can set everything as a result of a function that avoids changing states and mutating data.

- Reactive Programming: Reactive programming is a programming paradigm with asynchronous data streams or event streams. An event stream can be anything like keyboard inputs, button taps, gestures, GPS location updates, accelerometer, iBeacon etc. Here, we can listen to a stream and react to it according to the situation.
