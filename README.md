# RxSwiftsdsd
This repo for test rxswift

# Observable Sequences
exampleOf("just") {

    let observable = Observable.just("Hello, world!")
    observable.subscribe { (event: Event<String>) in
        print(event)
    }
}

exampleOf("of") {

    let observable = Observable.of(1, 2, 3)
    observable.subscribe {
        print($0)
    }
    
    observable.subscribe {
        print($0)
    }

}

exampleOf("toObservable") {

    let disposeBag = DisposeBag()
    
    [1, 2, 3].toObservable()
        .subscribeNext {
            print($0)
    }
    .addDisposableTo(disposeBag)
    
    [4, 5, 6].toObservable()
        .subscribeCompleted {
            print("Completed")
    }
    .addDisposableTo(disposeBag)
}

exampleOf("error") {

    enum Error: ErrorType {
        case Test
    }
    
    Observable<Int>.error(Error.Test)
        .subscribe {
            print($0)
    }
}

