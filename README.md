
# What are Reactive Extensions_

https://viblo.asia/xuanduc987/posts/YrEBRANlM8Zj
# RxSwift
Playground with lib:

https://github.com/segiddins/ThisCouldBeUsButYouPlaying/tree/master/bin

https://medium.com/@_achou/making-a-playground-using-rxswift-81d8377bd239#.vkoroyfh6

http://rxmarbles.com/

#Common Patterns
Observer

Iterator

#Lifecycle of an Observable Sequence
.Next

.Error

.Complete

.dispose()/DisposeBag()

# Observable Sequences
exampleOf("just") {

    let observable = Observable.just("Hello, world!")
    observable.subscribe { (event: Event<String>) in
        print(event)//Next(Hello, world!)
    }
}

exampleOf("of") {

    let observable = Observable.of(1, 2, 3)
    observable.subscribe {
        print($0)
    }// Next(1), Next(2), Next(3), Completed
    
    observable.subscribe {
        print($0)
    }

}

exampleOf("toObservable") {

    let disposeBag = DisposeBag()
    
    [1, 2, 3].toObservable()
        .subscribeNext {
            print($0)//1, 2 ,3
    }
    .addDisposableTo(disposeBag)
    
    [4, 5, 6].toObservable()
        .subscribeCompleted {
            print("Completed")//Completed
    }
    .addDisposableTo(disposeBag)
}

exampleOf("error") {

    enum Error: ErrorType {
        case Test
    }
    
    Observable<Int>.error(Error.Test)
        .subscribe {
            print($0)//Error(Test)
    }
}
//checkOut: http://reactivex.io/documentation/operators.html
