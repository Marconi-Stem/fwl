---
title: Notes
author: MCC
date: 2025-06-17
category: Notes
layout: post
---


https://gettingunstuck.gse.harvard.edu/


## 2. Hardware  
### 2.1 Supplies list


## 3. Software  
  - Create directions for installing:
    1. [Thonny](https://thonny.org/) for beginners, See thonny video, https://www.youtube.com/watch?v=bdvYIumllx8
    3. [PyCharm](https://www.jetbrains.com/pycharm/download/)
    4. [Circup](https://pypi.org/project/circup/)

## 4. Directions for upgrading the Circuit Python located on the Gemma M0 board. 

  - [Prof. G Youtube Channel](www.youtube.com/@BuildWithProfG)
  - [CircuitPython School](https://www.youtube.com/playlist?list=PLBJJ76R_ry5T3X72OIDkMOXQIdmcvSkue)

## 5. Circuit Python code for Neotrellis

  - Latest stable release for the Gemma M0: 
  - [https://circuitpython.org/board/gemma_m0/](https://circuitpython.org/board/gemma_m0/)

## 6. Introduction to Circuit Python
  - Commands contained in Firewalker code.
  - [https://circuitpython.org/](https://circuitpython.org/)

  - Import 

---


4. [Scratch-YouTube](https://www.youtube.com/@ScratchTeam)


1. [Meet Google programmers](https://www.youtube.com/shorts/UvpGHZw79DA)
   
2. [Try Scratch Team-1](https://www.youtube.com/watch?v=jXUZaf5D12A)

3. [Watch Scratch Team-2](https://www.youtube.com/watch?v=98awWpkx9UM)
   
---


# 1. Introduction



To prepare our *Neotrellis* we have X steps:

1. Join Scratch and Learn Programming Basics
2. Download & Install Windows driver
3. Download & Install .UF2
4. Download & Install Thonny
5. Download & Install Circup
6. Setup Python on your computer,


[Goto: 1099373392](https://scratch.mit.edu/projects/1099373392/)


---

![2 Scientists](/images/scratch.png/2scientists.png)<br>Is '*Abracadabra*' a valid command in this computer language?

---

Templates for certificates

https://create.microsoft.com/en-us/templates/certificates


==================================
FOR TEACHERS:

  * Welcome & Icebreaker: What is programming? Why learn it?
  * Introduction to Scratch:
    * Sign-up class to Scratch Act
    * Interface overview (Sprites, Stage, Blocks Palette, Scripts Area).
      * Basic movement & animation (e.g., moving a sprite, changing costumes).
      * Understanding Sequencing of commands.
   * Hands-on Activity: Create a simple animated story or a sprite that moves across the screen.

### B. Control Flow & Interactivity

   * Loops:
      * Introduce *repeat blocks*, avoid repetitive code.
      * Hands-on Activity: Make a sprite draw a shape using loops.
   * Conditionals or Branching:
      * Introduce *if* and *if/else* blocks for decision-making.
      * Hands-on Activity: Create a simple game where a sprite reacts to touching another object or a specific color.
   * Events or Inputs:
      * Explore when *green flag* clicked, when *key pressed*, when *sprite clicked blocks.
   * Project: Students create a short interactive game or story incorporating loops, conditionals, and events.

============================

 Three-Day Summer Programming Class: From Scratch to Microcontroller

**Summary**: This document outlines a progressive learning journey for students, starting with foundational concepts in Scratch and culminating in practical Python programming on a microcontroller board.


## Day 1: Visual Programming Fundamentals with Scratch

**Objective**: Introduce core programming concepts through a fun, interactive, block-based environment.

### A. Introduction & Basics with Scratch

  * Welcome & Icebreaker: What is programming? Why learn it?
  * Introduction to Scratch:
    * Sing up class to Scratch Act
    * Interface overview (Sprites, Stage, Blocks Palette, Scripts Area).
      * Basic movement & animation (e.g., moving a sprite, changing costumes).
      * Understanding Sequencing of commands.
   * Hands-on Activity: Create a simple animated story or a sprite that moves across the screen.

### B. Control Flow & Interactivity

   * Loops:
      * Introduce *repeat blocks*, avoid repetitive code.
      * Hands-on Activity: Make a sprite draw a shape using loops.
   * Conditionals or Branching:
      * Introduce *if* and *if/else* blocks for decision-making.
      * Hands-on Activity: Create a simple game where a sprite reacts to touching another object or a specific color.
   * Events or Inputs:
      * Explore when *green flag* clicked, when *key pressed*, when *sprite clicked blocks.
   * Project: Students create a short interactive game or story incorporating loops, conditionals, and events.

## Day 2: Bridging to Python - Concepts & Syntax

**Objective**: Transition from visual blocks to text-based code, understanding how Scratch concepts translate into Python syntax.

### Concept Translation & Python Introduction
   * Review Scratch Concepts: Briefly recap sequencing, loops, and conditionals.
   * "Bridge" Scratch blocks to text commands.
   * Introduction to Python:
      * What is Python? Where is it used (web, data, AI)?
      * Setting up a basic Python environment (e.g., online interpreter, simple IDE like Thonny).
      * Basic Python Syntax:
         * print() function for output.
         * Variables: Storing data (e.g., name = "Alice", age = 12).
         * Data Types: Numbers (integers, floats) and Strings.
         * Arithmetic Operations: +, -, *, /.
   * Hands-on Activity: Write simple Python scripts to print messages, store values in variables, and perform basic calculations.
* Python Control Flow
   * Loops in Python:
      * for loops (e.g., iterating through a range of numbers).
      * while loops (e.g., repeating until a condition is met).
      * Hands-on Activity: Write programs that use loops (e.g., counting, simple patterns).
   * Conditionals in Python:
      * if, elif, else statements for decision-making.
      * Hands-on Activity: Create a simple "choose your own adventure" text game or a program that checks if a number is even/odd.
   * User Input:
      * Using the input() function to get data from the user.
   * Project: Develop a simple console-based Python game (e.g., a "guess the number" game, a simple calculator).

## Day 3: Microcontroller Programming with Python (Micro:bit)

**Objective: Apply Python knowledge to interact with physical hardware, bringing code to life.**

* Micro:bit Setup & Basic I/O
   * Introduction to Micro:bit:
      * What is a microcontroller? What can it do?
      * Overview of Micro:bit components (LED matrix, buttons, sensors, pins).
   * Setting up MicroPython:
      * Connect the Micro:bit.
      * Use the online Micro:bit Python editor or Thonny IDE.
      * Flashing MicroPython firmware (if necessary).
   * Basic Micro:bit Programming:
      * Displaying text and images on the LED matrix (display.scroll(), display.show()).
      * Reading button presses (button_a.is_pressed(), button_b.was_pressed()).
   * Hands-on Activity: Make the Micro:bit display a message, then change it when a button is pressed.
* Sensors & Final Project
   * Built-in Sensors:
      * Explore using the accelerometer (accelerometer.get_x(), get_y(), get_z()).
      * Light sensor (display.read_light()).
      * Temperature sensor (temperature()).
   * Combining Concepts: Integrate loops, conditionals, and sensor readings.
   * Project Development: Students choose and build a small project:
      * Digital Dice: Shake the Micro:bit to display a random number.
      * Light-Activated Alarm: Display a message or play a tune when it gets dark/light.
      * Step Counter: Use the accelerometer to count steps.
      * Rock, Paper, Scissors: Use button presses and display.
   * Showcase & Review: Students demonstrate their projects, discuss challenges and successes.
   * Next Steps: Resources for continued learning (online tutorials, other micro-controllers).
