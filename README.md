# qsim
Batch queue simulator
Just a little hack for a one-time task.  Nothing very interesting here.

How it works:
- run ./qsim (need to have Term::ANSIScreen perl module installed)
- preload queue (either random) or when starting simulator by passing create instructions
  ./qsim 10hj 10hJ 5mj 30s 5lJ <br>
this creates:<br>
   10 high prio jobs (small files 10k)<br>
   10 high prio jobs (big files 512MB)<br>
   5  med  prio jobs (small)<br>
   30 second pause<br>
   5  low  prio jobs (big)<br>

when running qsim, the flow can be controlled via keystrokes:
* c - clear the que
* p - pause/unpause
* q - quit simulator
* t - drop and reconnect tunnel
* f - faster
* F - much faster
* s - slower
* S - much slower
* a - toggle the algorithm (current <-> proposed)
* j - create small upload job (10k)
* J - create big upload job (512MB)
* l - next job to create has low prio
* m - next job to create has med prio
* h - next job to create has high prio
* 1..0 - define number of jobs to create

- current algorithnm<br>
   polls que every 30s and checks for free upload slots<br>
   picked jobs are sorted by prio first and then runtime<br>
<br>
- new algorithm<br>
   as soon as a slot is available it is used for uploads<br>
   pick due jobs sorted by prio first and then submit-time<br>

