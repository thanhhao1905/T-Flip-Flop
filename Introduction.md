
# Introduction to the `t_ff_sync_rst_n` Module

## Overview
This repository contains a **T-Flip Flop (Toggle Flip-Flop)** with a synchronous, active-low reset.

The **T-Flip Flop** is a fundamental sequential logic circuit that changes its output state on each clock edge when its **Toggle (T)** input is high. It gets its name from its ability to "toggle" its output.

* When the **T** input is **low (0)**, the flip-flop holds its current state (Q remains unchanged) on the rising edge of the clock.
* When the **T** input is **high (1)**, the flip-flop toggles its output state (Q changes from 0 to 1, or from 1 to 0) on the rising edge of the clock.

This design is implemented with a **synchronous, active-low reset**. This means that when the **`rst_n`** input is low, the flip-flop's output **Q** will be reset to `0` on the next rising edge of the clock. This design is robust because the reset action is synchronized with the clock, which helps prevent timing issues and ensures predictable behavior in larger digital systems.

## Key Features

| Port Name | Function | Notes |
| :--- | :--- | :--- |
| **T** | Toggle | Toggles the output Q when T=1 |
| **clk** | Clock | Synchronous clock signal |
| **rst_n** | Synchronous Reset | Resets Q to 0 on the rising clock edge when active low |
| **Q** | Main Output | The primary output of the flip-flop |
| **Q_n** | Inverted Output | The inverted output of the flip-flop |

## Design Goal
The primary goal of this project is to provide a clean, simple, and reusable T-Flip Flop module. This design is highly suitable for building frequency dividers, counters, and other common sequential circuits. The inclusion of a synchronous reset makes this module ideal for educational purposes and for integration into more complex digital logic designs where predictable state initialization is critical.
