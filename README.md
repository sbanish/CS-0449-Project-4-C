## Project Description
Standard UNIX and Linux systems come with a few special files like /dev/zero, which returns nothing but zeros when it is read, and /dev/random, which returns random bytes. In this project, you will write a device driver to create a new device, /dev/dice which returns a randomly selected roll of a 6-sided die.

## How It Will Work
For this project we will need to create three parts: the device driver, the special file /dev/dice, and a test program to convince ourselves it works

The test program will be a solitaire implementation of the game of yahtzee.

## Driver Implementation
Our device driver will be a character device that will implement a read function (which is the implementation of the read() syscall) and returns an appropriate die roll (a 1 byte value from 0 to 5). As we discussed in class, the kernel does not have the full C Standard library available to it and so we need to get use a different function to get random numbers. By including <linux/random.h> we can use the function get_random_bytes(), which you can turn into a helper function to get a single byte

## Yahtzee Implementation
Yahtzee (also known as Poker Dice) is a multiplayer dice game, with fairly simple rules. For this assignment, you will be implementing a solitaire version where a user plays by themself. I highly suggest playing the game or at least reading the rules http://en.wikipedia.org/wiki/Yahtzee

5 dice are rolled. The player can choose to keep any of the dice and is allowed to reroll any they do not want to keep. They may reroll up to twice, but at the end of the third roll, the five dice are finalized.

After the user has finalized their five dice, they may place them into one of N categories.
