---
title: "Proof of Concept: PyTBV to Stream Transactions from CSV"
published: false
---
Building on my earlier effort to get [cocotb and pyuvm running without a real simulator](https://www.linkedin.com/pulse/first-step-towards-pytbv-breaking-simulator-dependence-hong-ping-tan-niitc/?trackingId=41U15zDyrmApv9Xb0PmicA%3D%3D), I’ve added another kernel that streams recorded transactions from a CSV directly into a pyuvm agent. The implementation is now available in the [PyTVB repository](https://github.com/hongping/pytbv). One more twist this time: the entire development happened inside Google’s new Antigravity, with most of the coding driven by Gemini 3 Pro. I’ll share more about that experience in a separate post.

With this kernel in place, it’s showed clearly that recorded transactions can be replayed in an offline, structured UVM-style environment, allowing verification work to continue without depending on a real simulator. As long as transactions are captured, new checks can be built, coverage can be added, and multiple iterations can be carried out quickly.

* * *

# Some Technical Details

Let’s dig into a bit of the technical side. The code below shows a typical UVM monitor, whether in Python or SystemVerilog, the idea is the same. Normally, the monitor watches a signal or port and captures transactions when activity occurs. In the PyTBV CSV-streaming setup, this behavior is replaced with a custom trigger, `CsvTrigger`, which drives the monitor based on CSV-recorded events instead of DUT signal changes.

```
class Producer(uvm_component):
    def __init__(self, name, parent):
        super().__init__(name, parent)
    
    def build_phase(self):
        self.put_port = uvm_blocking_put_port("put_port", self)

    async def run_phase(self):
        # Loop until simulation ends
        while True:
            self.logger.info(f"Waiting for CSV transaction")
            try:
                # Wait for trigger from CSV on Port "A"
                t = await CsvTrigger("A")
                
                # Create UVM transaction
                tr = UvmTransaction()
                tr.address = t.transaction.address
                tr.data = t.transaction.data
                
                self.logger.info(f"Received from CSV: {tr}")
                
                # Send to consumer
                await self.put_port.put(tr)
                
            except Exception as e:
                self.logger.error(f"Error waiting for transaction: {e}") 
```

Once the CSV kernel detects a transaction destined for the target port, port A in this case, the trigger is fired. The monitor loop resumes from that point, with the transaction data supplied through the trigger’s return value. The example can be found in the repository - `tests/test_pyuvm_csv.py`