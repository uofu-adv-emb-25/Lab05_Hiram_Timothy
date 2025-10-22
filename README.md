# Renode setup
The Raspberry Pico needs configuration files for Renode to work properly.

* On MacOS, the installation location is `/Applications/Renode.app/Contents/MacOs`
* On Linux, the location for Debian, Fedora, and Arch is `/opt/renode`
* On Windows, the location is `C://Program Files/Renode`

To add the Pico configuration files:
1. Copy `rp2040_spinlock.py` and `rp2040_divider.py` to the `scripts/pydev` directory of your Renode installation.
1. Copy `rpi_pico_rp2040_w.repl` to the `platforms/cpus` directory.


Timekeeping Measurements
========================================================================= timer.c =========================================================================
Results for timer.c without the precense of a busy loop and a delay of 10 ms, the oscilloscope gives a period of 20.0008 ms, the expected result is 20 ms, this is an accurate result.

Results for timer.c with a delay of 10 ms and a busy loop containing 2 million instructions (for(i <1_000_000...)), the oscilloscope gives a period of 96.004 ms, expected 20 ms

========================================================================= sleep.c =========================================================================
Results for sleep.c without the precense of a busy loop and a delay of 10ms, the oscilloscope gives a period the same result as timer.c, being 20.0008 ms, the expected result us 20 ms, this is an accurate result.

Results for sleep. with a delay of 10 ms and a busy loop containing 2 million instructions (for(i <1_000_000...)), the oscilloscope gives a period of 116.0028 ms, expected 20 ms, this is considerably different compared to timer.c when a busy loop is added.

======================================================================= task_delay.c =======================================================================
Results for task_delay.c without the precense of a busy loop and a delay of 10ms, the oscilloscope gives a period the same result as timer.c and sleep.c, being 20.0008 ms, the expected result us 20 ms, this is an accurate result.

Results for task_delay with a delay of 10 ms and a busy loop containing 2 million instructions (for(i <1_000_000...)), the oscilloscope gives a period of 116.005 ms, expected 20 ms, this is considerably different compared to timer.c, however similar to sleep.c. when a busy loop is added.

Jitter Measurements
========================================================================= timer.c =========================================================================
Without Busy loop: Drift =  .004% faster, StdDev/Jitter = 0 s
With Busy loop: Drift =  79.167599 % slower, StdDev/Jitter = 0 s

========================================================================= sleep.c =========================================================================
Without Busy loop: Drift = .03998 % slower, StdDev/Jitter = 0 s
With Busy loop: Drift =  82.7590 % slower, StdDev/Jitter = 19.136 us

======================================================================= task_delay.c =======================================================================
Without Busy loop: Drift = .03998 % slower, StdDev/Jitter = 0 s
With Busy loop: Drift = 82.7593 % slower, StdDev/Jitter = 0 s

