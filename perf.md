# perf

`perf stat -d ./my_program_to_perf`

High level stats of the program (branch predicition, cycles, cache miss, etc)

---
Report where program is spending most of its time (what part of the program is being used the most)

`perf record ./my_program_to_perf`

`perf report`

---