---
title : thoughts on machine readable specification
categories:
- thoughts
tags:
- dsl
- specification language 
---

Specification is the most important part of a hardware design. RTL coders will code the HDL model based on the specication, while validators will use the specification to create test plan to verify the design. Circuit designers will need the specification to better draft the floor plan as well as meeting the timing and electrical requirements. Specifications is the **golden reference** for all parties in a design flow. Hence, it is very important that the specification is clear, accurate and without ambiguity.
{: style="text-align: justify;"}

Most of the specifications are provided as documentation in natural languages, e.g. [RISC-V specifications](https://riscv.org/specifications) and [I2C specification](https://www.nxp.com/docs/en/user-guide/UM10204.pdf). Some specifications provided pseudo code, e.g. [Intel Software Developer Manual](https://software.intel.com/en-us/articles/intel-sdm). Won't it be great if the specification is provided in a machine readable format, and automations can be created to act on the parsed specification? For e.g. test cases generation, behavioural model creation, or even RTL code generation?
{: style="text-align: justify;"}

Thus far, only ARM provided a machine readable specification in [XML format](https://developer.arm.com/architectures/cpu-architecture/a-profile/exploration-tools). Following Alastair Reid's [work](https://alastairreid.github.io/ARM-v8a-xml-release/), it seemed that ARM has been using the XML specification for formal verification purpose.
{: style="text-align: justify;"}

This triggered me to create something similar for RISC-V, since I have been wanting to work on RISC-V. I am trying to work out now what need to be precisely describe in a specification, and how a domain specific language (DSL) can be crafted out for this purpose. The first stop will be looking at what ARM has, and also doing more literature research on others.
{: style="text-align: justify;"}

The end goal I have in mind is a standardized DSL for all specifications, though I think it will be a far reach goal. But who knows, right? Shoot for the moon and if you miss you will still be among the stars. 
{: style="text-align: justify;"}

One doubt I have on machine readable specification, is that it created another source of uncertainty and it required extra verification. The reasoning is that natural language documents will still be provided, and if there is a conflicting statement between the two, we have a big problem. The users will not know which to follow, since ideally both are the golden reference. Besides that, imagine a scenario where the machine readable specification is out of sync, or outdatated. Any tools or codes that depends on that may not produced expected outcomes. Hence, it is vital to verify the machine readable specification is equivalent to the natural language documentation. The other way to solve this will be generating natural language documentation out of the specification. That will be another big topic to ponder on.
{: style="text-align: justify;"}

As for now, I will focus on getting started :)
{: style="text-align: justify;"}