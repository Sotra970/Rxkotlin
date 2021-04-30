
	
RX knowledge base 

Gradle implementaion 

    // RxJava2 Dependencies
    implementation("io.reactivex.rxjava2:rxkotlin:2.2.0")

> **1-STREAM TYPES(observables )**

  

	   1. Observable: emit a stream elements (endlessly) 
	   2. Flowable: emit a stream of elements (endlessly, with backpressure) 	
	   3. Single: emits exactly one element 	 	
	   4. Maybe: emits zero or one elements 	
	   5. Compelteable: emits a “complete” event, without emitting any data type, just a success/failure
     

> **2- Observer :**

-  Observer has 4 interface methods to know the different states of the Observable: 

		1-onSubscribe(): This method is invoked when the Observer is subscribed to the Observable.
		
		2-onNext(): This method is called when a new item is emitted from the Observable.
		
		3-onError(): This method is called when an error occurs and the emission of data is not successfully completed.
		
		4-onComplete(): This method is called when the Observable has successfully completed emitting all items.



> **3-SUBJECTS :**
 - abstract (which means it doesn’t provide an implementation) but the framework provides several default implementations that can be super-useful.

	**1. Publish Subject:**
 
	 - it doesn’t cache any event,so notifications about past elements aren’t forwarded to each new observer.
	 -   Once the PublishableSubject emits an error, all the subscribers are notified and won’t receive anything more. 
	   -   A PublishableSubject is useful, for instance, in bypassing hardwar events like  		scroll positions, mouse events, clicks, etc… 
	    - so yo can subscribe several observers to them 		but you just want to listen out for newer events.
	    ![PublishSubject](http://reactivex.io/documentation/operators/images/S.PublishSubject.e.png)

	**2.  Replay:**
	 - replays events to current and late observers, and it can be created in several ways:
**1. create:** unbounded subject that replays everything
**2. createWithSize(int):** only retains the amount of items indicated.
**3. createWithTime(int, TimeUnit):** retains only objects contained in the specified time window.
**4.  createWithTimeAndSize:** This is  combination of 2 and 3 

	
	![ReplaySubject](http://reactivex.io/documentation/operators/images/S.ReplaySubject.png)

	**3. BehaviorSubject:**
	
	 -  used in Android’s Presenters/ViewModels, is quite similar to the PublishSubject
	 - caches the most recent value emitted(deliver last emitted value to new subscriber)
	 ![BehaviorSubject](http://reactivex.io/documentation/operators/images/S.BehaviorSubject.png)
	
	![BehaviorSubject](http://reactivex.io/documentation/operators/images/S.BehaviorSubject.e.png)


	
	**4. AsyncSubject :**
  
	 - caches the last event emitted and sends it to the observers only when an onComplete event is emitted.
	 - This subject can be used when we don’t care about the data stream, only the last object.
	 
	 
	 ![AsyncSubject](http://reactivex.io/documentation/operators/images/S.AsyncSubject.png)


	![AsyncSubject](http://reactivex.io/documentation/operators/images/S.AsyncSubject.e.png)

> **4-OPERATORS**

**1-Creating Observables**

 - **1. Create:**
	  - operator creates an Observable from scratch 
	- next > next >  .. compelete
	- 
![create](http://reactivex.io/documentation/operators/images/create.c.png)
		-  [see more](http://reactivex.io/documentation/operators/create.html)
- **2. Defer:** 
	- The Defer operator waits until an observer subscribes to it,
				and then it generates an Observabl
	- So you can create multi-value observable based on state at time of subscription
	- Note : fromCallable: creates observable that emits single value, then completes.	
	![enter image description here](http://reactivex.io/documentation/operators/images/defer.c.png)
				
		- [see more](http://reactivex.io/documentation/operators/defer.html)
			
			
			

> **credits :**
- http://bugfender.com/blog/data-flows-in-rxjava2-observable-flowable-single-maybe-completable/
- http://www.raywenderlich.com/my-tutorials
- **useful links :**
	- doonerror :
		-  http://stackoverflow.com/a/33670742/6435871
	- networking :
		- http://jakewharton.com/the-state-of-managing-state-with-rxjava/
	- error handling :
		-  http://www.baeldung.com/rxjava-error-handling

