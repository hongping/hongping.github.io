---
title: "Proof of Concept: PyTBV to Stream Transactions from CSV"
published: false
---
Building on my earlier effort to get [cocotb and pyuvm running without a real simulator](https://www.linkedin.com/pulse/first-step-towards-pytbv-breaking-simulator-dependence-hong-ping-tan-niitc/?trackingId=41U15zDyrmApv9Xb0PmicA%3D%3D), I’ve added another kernel that streams recorded transactions from a CSV directly into a pyuvm agent. The implementation is now available in the [PyTVB repository](https://github.com/hongping/pytbv). One more twist this time: the entire development happened inside Google’s new Antigravity, with most of the coding driven by Gemini 3 Pro. I’ll share more about that experience in a separate post.

With this kernel in place, it’s now clear that recorded transactions can be replayed in an offline, structured UVM-style environment, allowing verification work to continue without depending on a real simulator. As long as transactions are captured, new checks can be built, coverage can be added, and multiple iterations can be carried out quickly.