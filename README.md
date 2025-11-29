
---

# D Flip-Flop Verification Using SystemVerilog Layered Testbench

This project demonstrates how a **D Flip-Flop (D-FF)** is verified using a **SystemVerilog layered testbench**.
It is designed for students and beginners who want to understand both **digital design** and **verification methodology** in a simple, clear way.

---

# 1. What Is a D Flip-Flop?

A **D Flip-Flop** (Data or Delay flip-flop) is one of the most fundamental storage elements in digital electronics.

### **Function**

A D-FF stores the value of input **D** on the **rising edge** of the clock **CLK** and holds it until the next rising edge.

### ✔ Truth Table

| Clock (↑ edge) | D | Q(next) |
| -------------- | - | ------- |
| Rising Edge    | 0 | 0       |
| Rising Edge    | 1 | 1       |

### ✔ Behavior

* When `CLK` goes from **0 → 1**, the output **Q** takes the value of **D**
* Between clock edges, **Q remains constant**

It is used in:

* Registers
* Counters
* State machines
* Pipelines
* Memory elements

---

# 2. Why Do We Verify a D Flip-Flop?

Even simple circuits need proper verification to ensure:

* Correct functionality
* No glitches
* Timing behavior matches specification
* Output is stable and predictable

Verification becomes even more important for **large digital systems**, so learning it on a small design is the best way to start.

---

# 3. What Is a Testbench?

A **testbench** is code written to test hardware designs.
It generates inputs, drives them to the DUT (Design Under Test), observes outputs, and checks correctness.

But testbenches can be written in two styles:

1. **Simple (flat) testbench**
2. **Layered (modular, scalable) testbench**

---

# 4. What Is a Layered Testbench?

A **layered testbench** breaks the testbench into multiple logical components, each responsible for a specific function.

This is the same idea used in UVM (Universal Verification Methodology), but simplified.

### ✔ Components of a Layered Testbench

| Layer           | Role                                       |
| --------------- | ------------------------------------------ |
| **Transaction** | Holds input/output data                    |
| **Generator**   | Creates random or directed test values     |
| **Driver**      | Drives inputs to the DUT through interface |
| **Monitor**     | Observes DUT outputs                       |
| **Scoreboard**  | Compares expected vs actual output         |
| **Environment** | Connects all components together           |
| **Test**        | Starts the simulation                      |

This structure makes the testbench:

* Scalable
* Reusable
* Easy to debug
* Modular
* Suitable for complex verification

---

# 🔰 5. Project Structure

```
├── design.sv          # D Flip-Flop RTL
├── interface.sv       # Connects DUT with the testbench
├── transaction.sv     # Class describing input/output transaction
├── generator.sv       # Creates random stimulus
├── driver.sv          # Sends data to DUT
├── monitor.sv         # Observes DUT output
├── scoreboard.sv      # Checks correctness
├── environment.sv     # Top-level testbench environment
├── test.sv            # Test scenario
├── testbench.sv       # Central testbench module
└── run.do             # Script for QuestaSim (EDA Playground)
```

---

# 🔰 6. How the Verification Works (Simple Explanation)

### **Step 1: Generator creates a random D value**

Example:

```
d = 0
```

### **Step 2: Driver sends D to the DUT**

Driver applies the value to the interface connected to the flip-flop.

### **Step 3: Flip-Flop updates Q on the clock edge**

If rising edge → Q becomes D.

### **Step 4: Monitor reads Q and reports it to Scoreboard**

Monitor observes the output and sends it to the scoreboard.

### **Step 5: Scoreboard checks expected vs actual**

If D=1 at clock edge, Q must be 1.
If D=0 at clock edge, Q must be 0.

### **Step 6: Coverage is recorded**

Covergroups check whether both 0 → 0 and 1 → 1 cases were hit.

---

# 7. Simulation Results

✔ Successful compile
✔ Scoreboard matched expected behavior
✔ Functional coverage reached **100%**
✔ Results printed:

```
Result is as Expected
d = 0, q = 0
Result is as Expected
d = 1, q = 1
```

The testbench fully verifies the DUT.

---

# 8. Tools Used

* **SystemVerilog**
* **QuestaSim / ModelSim via EDA Playground**
* Timescale: `1ns / 1ns`

---

# 9. Why This Project Is Useful

This project helps beginners understand:

* Basic flip-flop behavior
* Hardware verification flow
* Object-oriented SystemVerilog
* Functional coverage
* Self-checking testbenches
* Layered testbench design
* How professional verification environments are built

It’s a perfect starting point before learning **UVM**.

---

#  10. Conclusion

This project shows a complete verification flow for a simple D Flip-Flop using a clean, modular, layered testbench.
It demonstrates the importance of structured verification and modern methodologies in digital design.

Feel free to explore, modify, and expand this repository to learn more about digital verification.

---

If you want, I can also create:

* A README banner
* GitHub badges
* A diagram showing your testbench architecture
  Just tell me!
