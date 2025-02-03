# Basic Logic

## Crude Awakening

> A signal flows from the input to the output.

![Signal](./assets/basic_logic/crude_awakening.png)

The first level teaches us that when activating the input, the signal will flow to the output.

## NAND Gate

We learn about the first logic gate! It's called the `NAND` gate. Everything in a computer can be constructed from this gate. In this level we have to find out how the two input bits influence the output.

A `NAND` gate always returns **1** except when both inputs are **1**. This is the truth table:

| A   | B   | Out |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   |

![NAND gate](./assets/basic_logic/nand_gate.png)

## NOT Gate

The `NOT` gate simply inverts the input. So when the input is **0** the output will be **1**. If the input is **1** then the output will be **0**.

We can build a `NOT` gate by connecting the input to the two pins of the `NAND` gate.

![NOT gate](./assets/basic_logic/not_gate.png)

## AND Gate

The `AND` gate is simply an inverted `NAND` gate. That's why it's called `NAND` gate: **NOT** `AND`. So all we have to do is simply inverting the output of `NAND` with a `NOT` gate we obtained in the last level.

![AND gate](./assets/basic_logic/and_gate.png)
