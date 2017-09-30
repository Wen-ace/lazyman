# lazyman
use a array to simulate stacks

simple method
/ ********************************* /
 var tasks = [];
    function next() {
        console.log(tasks);
        var fn = tasks.shift();
        fn && fn();
    }
    function init() {
        var fn = (function () {
            return function () {
                setTimeout(function () {
                    next();
                }, 0)
            }
        })();
        tasks.push(fn);
        next();
        return this;
    }
    function first() {
        var fn = (function () {
            return function () {
                setTimeout(function () {
                    console.log(1);
                    next();
                }, 1000);
            }
        })();
        tasks.push(fn);
        return this;
    }
    function two() {
        var fn = (function () {
            return function () {
                setTimeout(function () {
                    console.log(2);
                    next();
                }, 1000);
            }
        })();
        tasks.push(fn);
        return this;
    }

    init();
    two();
    first();
    / ******************************* /
