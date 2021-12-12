（1）实现满足重试请求的函数，返回一个符合要求的新request方法
<script>
    // retryRequest(request, 3, [100, 200, 300], res => res.code === 502)

    function retryRequest(request, times, list, checkFn) {

    }
</script>

（2）k个请求中有一个完成就会去执行下一个请求，全部完成会执行callback，请求方法可以用fetch

<script>
    // sendRequest(['/a', '/b', ...], 5, ()=>{}) 

    function sendRequest(urls, k, callback) {​

    }
</script>

（3）实现一个带并发限制的异步调度器Scheduler，保证同时运行的任务最多有两个。完善代码中Scheduler类，使得以下程序能正确输出。

<script>
    class Scheduler {
        tasks = []; // 所有任务
        runningTasks = []; // 运行中的任务

        add(promiseCreator) {
            
        }
    }
    const timeout = (time) =>
        new Promise((resolve) => {
            setTimeout(resolve, time);
        });

    const scheduler = new Scheduler();
    const addTask = (time, order) => {
        scheduler.add(() => timeout(time)).then(() => console.log(order));
    };

    addTask(1000, "1");
    addTask(500, "2");
    addTask(300, "3");
    addTask(400, "4");
    // output: 2 3 1 4
    // 一开始，1、2两个任务进入队列
    // 500ms时，2完成，输出2，任务3进队
    // 800ms时，3完成，输出3，任务4进队
    // 1000ms时，1完成，输出1
    // 1200ms时，4完成，输出4
</script>


注：promise面试知识点相关文章

https://juejin.cn/post/6844904077537574919