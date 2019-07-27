---
title : thoughts on architecture specification language
categories:
- thoughts
tags:
- dsl
- specification language 
---

Specification is the most important part of a hardware design. RTL coders will code the HDL model based on the specication, while validators will use the specification to create test plan to verify the design. Circuit designers will need the specification to better draft the floor plan as well as meeting the timing and electrical requirements. Specifications is the **golden reference** for all parties in a design flow. Hence, it is very important that the specification is clear, accurate and without ambiguity.
{: style="text-align: justify;"}

Won't it be great if the specification is provided in a machine readable format, and automations can be created to act on the parsed specification? For e.g. test cases generation, behavioural model creation, or even RTL code generation? However, most of the specifications are provided as documentation in natural languages, e.g. [RISC-V speficications](https://riscv.org/specifications) and [I2C specification](https://www.nxp.com/docs/en/user-guide/UM10204.pdf). Some specifications provided pseudo code, e.g. [Intel Software Developer Manual](https://software.intel.com/en-us/articles/intel-sdm). Thus far, only ARM provided a machine readable specification in [XML format](https://developer.arm.com/architectures/cpu-architecture/a-profile/exploration-tools).
{: style="text-align: justify;"}

Following [Alastair Reid](https://alastairreid.github.io/)'s work, it seemed that ARM has been using the XML specification for formal verification purpose. I think this is a great move, however, I have more doubts on this. To name a few:
1. HOw 
{: style="text-align: justify;"}