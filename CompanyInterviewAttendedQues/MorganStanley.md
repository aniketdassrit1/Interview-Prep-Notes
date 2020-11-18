* Write a digital clock app, with following requirement:
    * Should have features like Start, Stop and Pause
    * Count till 60sec

```
import { Component, OnDestroy, OnInit } from "@angular/core";
import { Subscription, timer } from "rxjs";

@Component({
  selector: "my-counter",
  templateUrl: "./my-counter.component.html"
})
export class MyCounter implements OnInit, OnDestroy {
  counter = 0;
  subs: Subscription;
  pauseState: boolean = false;

  ngOnInit(): void {}

  startCounter(): void {
    const source = timer(1000, 1000);
    this.subs = source.subscribe(() => {
      if (this.counter < 60) {
        this.counter = this.counter + 1;
      } else {
        this.stop();
      }
    });
  }

  start(): void {
    this.startCounter();
  }

  stop(): void {
    this.subs.unsubscribe();
    this.counter = 0;
    this.pauseState = false;
  }

  pause(): void {
    if (this.counter > 0) {
      this.pauseState = !this.pauseState;
      if (this.pauseState) {
        this.subs && this.subs.unsubscribe();
      } else {
        this.startCounter();
      }
    }
  }

  ngOnDestroy(): void {
    this.subs.unsubscribe();
  }
}

```

* How to make a secure api call
* What happens when you hit a weblink
* Angular security
* Different angular loading strategies, like lazy load, preload.
* Give a use case of lazy load.
