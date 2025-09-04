# 🖥️ Multi-Level Feedback Queue (MLFQ) CPU Scheduler Simulator

This project implements a **Multi-Level Feedback Queue (MLFQ) Scheduler** in Python.  
It simulates how processes are scheduled using **different priority queues**, **time quanta**, and **allotments**, along with **I/O handling** and **priority boosting**.  

The simulator allows you to experiment with parameters such as the number of queues, quantum lengths, job list, I/O times, and boosting intervals.

---

## 🚀 Features
- 🏷️ Supports **custom or random job generation**  
- ⏳ Handles **multiple queues with different quantum lengths and allotments**  
- 🔄 Implements **priority boosting**  
- 💾 Simulates **I/O operations and rescheduling**  
- 📊 Outputs **execution trace** and **final statistics** (response & turnaround times)  
- ⚡ Configurable using **command-line arguments**  

---

## 🛠️ Usage

Run the simulator:

```bash
python mlfq_scheduler.py [options]
````

### Options

* `-s`, `--seed` → Random seed (default = 0)
* `-n`, `--numQueues` → Number of queues (default = 3)
* `-q`, `--quantum` → Quantum length for each queue (if not using `-Q`)
* `-a`, `--allotment` → Time allotment per queue (if not using `-A`)
* `-Q`, `--quantumList` → Comma-separated quantum lengths per queue (highest → lowest)
* `-A`, `--allotmentList` → Comma-separated allotments per queue (highest → lowest)
* `-j`, `--numJobs` → Number of jobs (default = 3)
* `-m`, `--maxlen` → Max runtime of a job (default = 100)
* `-M`, `--maxio` → Max I/O frequency (default = 10)
* `-B`, `--boost` → Boost interval (default = 0 = no boosting)
* `-i`, `--iotime` → I/O duration (default = 5)
* `-S`, `--stay` → Stay at same level after I/O (default = False)
* `-I`, `--iobump` → Bump jobs to front of queue after I/O (default = False)
* `-l`, `--jlist` → Custom job list in format: `start,run,io:start,run,io:...`
* `-c` → Compute answers (show execution trace & statistics)

---

## 🧪 Examples

1. **Default 3 Queues, Random Jobs**

```bash
python mlfq_scheduler.py -n 3 -j 4 -m 50 -M 10 -c
```

2. **Custom Job List**

```bash
python mlfq_scheduler.py -l 0,20,5:0,15,3:0,10,0 -c
```

3. **Different Quanta per Queue**

```bash
python mlfq_scheduler.py -Q 8,16,32 -A 1,2,4 -c
```

4. **With Priority Boosting Every 20 Ticks**

```bash
python mlfq_scheduler.py -B 20 -j 5 -m 30 -M 5 -c
```

---

## 📊 Sample Output

```
Here is the list of inputs:
OPTIONS jobs 3
OPTIONS queues 3
OPTIONS allotments for queue  2 is   1
OPTIONS quantum length for queue  2 is  10
OPTIONS boost 0
OPTIONS ioTime 5

Job List:
  Job  0: startTime   0 - runTime  20 - ioFreq   5
  Job  1: startTime   0 - runTime  15 - ioFreq   3
  Job  2: startTime   0 - runTime  10 - ioFreq   0

Execution Trace:
[ time 0 ] Run JOB 0 at PRIORITY 2 [ TICKS 10 ALLOT 1 TIME 19 (of 20) ]
[ time 1 ] Run JOB 0 at PRIORITY 2 ...
...
Final statistics:
  Job  0: startTime   0 - response   0 - turnaround  25
  Job  1: startTime   0 - response   5 - turnaround  20
  Job  2: startTime   0 - response   2 - turnaround  10

  Avg: response 2.33 - turnaround 18.33
```

---

## 📂 Project Structure

```
📁 MLFQ-Scheduler-Simulator
│── mlfq_scheduler.py   # Main simulator code
│── README.md           # Documentation
```

---

## 👨‍💻 Author

* Hasan Zarook (2021-CE-58)

---

## 📜 License

This project is licensed under the **MIT License**.

```

