---
category: best-practice
sub_category_1: race-condition
language: de
tags:
- best-practice
- race-condition
---

## Race Condition

A race condition (a race to access resources) is an undesirable situation that occurs when a device or system attempts to perform two or more operations simultaneously. But because of the particular nature of each device or system, the operations must be performed in the correct order to be truly correct.

A simple example of a race condition is a light switch. In some houses or apartments, there are multiple light switches connected to a common overhead light. When these types of switches are used, the particular switch position becomes irrelevant. If the light is on, and you move any other switch from its current (on) position, the light will be turned off again. The situation is similar when the light is off: using each switch in its current position turns the light on. On this basis, one must now imagine what could happen if two people at two different switches try to switch on the light at exactly the same time. One switch action could turn off the other, or both simultaneous actions could result in a short circuit.

Race conditions are generally associated with computer science and IT. In computer memory or [[storage]], a race condition can occur when read and write commands for large amounts of data are received at nearly the same time and the device attempts to overwrite some or all of the old data while that old data is still being read. As a result, one or more of the following phenomena may occur: a computer crash, an unidentifiable "illegal operation," invocation and shutdown of a program, errors reading the old data, or errors writing the new data. A race condition can also occur when arrangements are not implemented in the correct order.

For example, suppose that two processes need to perform a bit flip (bit change) at a specific memory location. Under normal circumstances, the operation should proceed as follows:

<table><tbody><tr><td><p>Process 1</p></td><td><p>Process 2</p></td><td><p>Memory Value</p></td></tr><tr><td><p>Read value</p></td><td></td><td><p>0</p></td></tr><tr><td><p>Flip value</p></td><td></td><td><p>1</p></td></tr><tr><td></td><td><p>Read value</p></td><td><p>1</p></td></tr><tr><td></td><td><p>Flip value</p></td><td><p>0</p></td></tr></tbody></table>

Process 1 thus performs a bit flip by setting the memory value from 0 to 1. Process 2 then performs a bit flip and changes the memory value from 1 to 0.

In a race condition, these two processes lead to an overlap, and the sequence could possibly look like the following:

<table><tbody><tr><td><p>Process 1</p></td><td><p>Process 2</p></td><td><p>Memory Value</p></td></tr><tr><td><p>Read value</p></td><td></td><td><p>0</p></td></tr><tr><td></td><td><p>Read value</p></td><td><p>0</p></td></tr><tr><td><p>Flip value</p></td><td></td><td><p>1</p></td></tr><tr><td></td><td><p>Flip value</p></td><td><p>1</p></td></tr></tbody></table>

In this example, the bit has a closing value of 1, but should have a value of 0. This happens because the second process does not know that process 1 is performing a simultaneous bit flip.

### Wie man Race Conditions verhindert

In computer environments, race conditions can be prevented by prioritizing memory access. This means that the read command is always executed first and terminated if read and write commands are received at approximately the same time.

In a network, a race condition can occur when two users want to access an available channel at the same time and neither of the computers involved receives a notification that the channel is already busy before granting access. Statistically, this type of overlap is highly likely to occur in networks with long time delays - for example, those based on geostationary satellites. To prevent such a competitive situation from developing, one must design a priority scheme. This might consist, for example, of ensuring that the user whose username begins with an earlier letter in the alphabet (or a lower number) gets access first whenever two users attempt to access the system in a defined period of time. Hackers are able to exploit such sensitive race conditions and use them to gain unauthorized access to networks.

Race conditions also occasionally occur at logical access points (gates) when certain inputs conflict with each other. Because the output of the gate takes a certain amount of time to respond to any change in the inputs, sensitive networks or devices behind the gate can be deceived about the current state of the output and therefore fail to function correctly.
