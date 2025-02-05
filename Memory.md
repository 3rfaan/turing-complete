# Memory

## Circular Dependency

> Make a circuit where the input of a component depens on its own output

![Circular Dependency](./assets/memory/circular_dependency.png)

## Delayed Lines

In this level we get a new component: the **Delay Line** component. It takes its input and outputs it one tick later. The assignment is to delay the output by two ticks.

All we have to do is chain two **Delay Line** components together. The input signal is delayed by two ticks before it reaches the output.

![Delayed Lines](./assets/memory/delayed_lines.png)

## Odd Ticks

In this level we learn that when using the **Delay Line** component, it is acceptable to have a circular dependency. This is because the input does not influence the rest of the circuit until next tick.

To test this we can use a **Delay Line** and connect its output to its own input before outputting it to the **Output** component. Before connecting it to its input we use a `NOT` gate to invert the input. This way, the output is only **1** when the tick is odd.

| Tick | Output |
| ---- | ------ |
| 0    | 0      |
| 1    | 1      |
| 2    | 0      |
| 3    | 1      |
| 4    | 0      |
| 5    | 1      |

![Odd Ticks](./assets/memory/odd_ticks.png)

## Bit Inverter

Two 1-bit inputs are given in this level:

**Value**: 0 or 1
**Invert**: No (0) or Yes (1)

Let's look at the truth table:

### Bit Inverter Truth Table

| Value | Invert | Out |
| ----- | ------ | --- |
| 0     | 0      | 0   |
| 1     | 0      | 1   |
| 0     | 1      | 1   |
| 1     | 1      | 0   |

The truth table looks exactly the same as the `XOR` truth table. So all we have to do is connecting both inputs to an `XOR` gate.

![Bit Inverter](./assets/memory/bit_inverter.png)

## Bit Switch

The assignment in this level is to create an `XOR` gate from two **Bit Switch** components and two `NOT` gates.

The **Bit Switch** component only outputs a signal when it is enabled. This means we can connect components which output different values on the same wire without getting an error.

When the top pin is **0** the output is disabled. The **Bit Switch** output will be gray meaning it does not emit any signal. We can connect as many switches and wires as we want as long only one of them is enabled at a time.

The logic is simple:

1. If **A** is 1, disable **B**
2. If **B** is 1, disable **A**

We achieve this by taking the signal of the disabled input which is **0**, then invert it and pass it to the switch of the enabled input. This way we allow the signal to flow through the **Bit Switch** only of the enabled input.

![Bit Switch](./assets/memory/bit_switch.png)

## Input Selector

We get three inputs: Two 8-bit numbers and a 1-bit **value** input. If the 1-bit **value** is **0**, select input **A**, otherwise **B**.

| Value | Out |
| ----- | --- |
| 0     | A   |
| 1     | B   |

When you take a look at the 8-bit components, you find in it an **8 Bit Switch**. This component allows us to take an 8-bit input and output it if the 1-bit **enable** pin is enabled (meaning **1**). Otherwise nothing will be outputted.

1. Connect the two binary numbers to the output. This will emit an error because we cannot write to the same wire at the same time.
2. Put on each wire an **8 Bit Switch**.
3. If **value** is **0** we invert the bit with a `NOT` gate and connect it to the switch for input **A**.
4. If **value** is **1** we connect it to the switch for input **B**.

This ensures that only one signal is emitted at a time to the same wire and the correct number will be outputted.

![Input Selector](./assets/memory/input_selector.png)
