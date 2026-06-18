# Daxo OS 🚀

A custom, independent x86_64 multitasking microkernel written in Rust from scratch.

Project Status: Active development. Built as an independent deep-dive into low-level operating system architecture.

<p align="center">
  <img src="screenshot.jpg" alt="Daxo OS Boot Screen" width="650">
</p>

## Key Features

Zero Standard Library (no_std): Runs on bare-metal with absolutely no underlying operating system dependencies.

Custom ATA Hard Drive Driver: Built an isolated PIO ATA driver to communicate directly with disk controllers via I/O ports before hardware interrupts are fully enabled.

Advanced Memory Management: Implements a 4-level paging architecture and a custom dynamic Heap Allocator supporting variable-length structures like Vec.

Cooperative Multitasking: Features a custom async Task Executor built leveraging Rust's Future and Waker types for non-blocking execution.

## Tech Stack

Language: Rust (Nightly channel)

Target Architecture: x86_64 (Custom JSON target specification)

Testing and Emulation: QEMU, Bootimage runner

## How to Run

To run this OS in a QEMU emulator, make sure you have Rust Nightly installed, then clone the repository and execute the following command:

cargo run -Zjson-target-spec

## 🧠 The Story Behind Daxo OS

This project wasn't just about following standard guides; it was a 100-hour focused development sprint balanced alongside high-intensity sports training and school. 

The real engineering began when step-by-step tutorials broke due to Rust Nightly updates, throwing complex linker errors (rust-lld: undefined symbol: memcpy) and Triple Faults. To solve this, I had to bypass high-level abstractions, dive deep into Cargo configuration flags, and manually manage core memory builtins.

To push the system further, I built an isolated PIO ATA hard drive driver from scratch to read disk sectors via raw I/O ports before hardware interrupts were even configured. Seeing the "Data read from LBA 0" log light up in QEMU proved that real software engineering starts exactly where the instructions end.
