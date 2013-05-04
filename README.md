#Description

This is a fork of [grunt-karma](https://github.com/karma-runner/grunt-karma). The only change I made is to bring back a behavior previously available. 

I wanted to get some feedback if my test are failing even when the console is minimized. 
I am running it with the `:run` flag within `grunt-watch` so I changed the callback from: 

```JavaScript
//support `karma run`, useful for grunt watch
if (this.flags.run){
    runner.run(data, done);
    return;
}
```
    
to: 
```JavaScript
//support `karma run`, useful for grunt watch
if (this.flags.run) {
     runner.run(data, finished.bind(done));
     return;
}
```

This way if there are failing tests it fires a warning to grunt and the task is aborted.

I saw in the issues that it was causing problems for some people, but for me it works like I want it to.