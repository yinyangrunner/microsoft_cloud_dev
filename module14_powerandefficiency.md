# Power and Efficiency #

## Check your knowledge ##

1. If a server's maximum power draw is 300 W and its idle power draw is 200 W, what is the approximate power draw at 5% utilization?

__205 W__

2. You have 200 servers in your organization, each with an average 10% CPU utilization, with Pidle of 200 W and Pmax of 300 W. If you virtualized these servers and consolidated onto 40 larger servers, each with Pidle of 250 W and Pmax of 800 W and an average utilization of 50%, How much power (in watts) would you save?

__21,000 W__

3. If the PUE of the datacenter is 2.0, and a server in this datacenter demands 500 W of power, what is the power (in watts) from the utility grid that is needed to deliver 500 W to the server?

__1,000 W__

4. The PUE is a measure of which of the following?

__How efficiently a datacenter uses power__

5. You have 12 servers, each with 1 PSU, measured to consume 500 W max. You also have three-phase 208-V PDUs with multiple branches, each branch with a 20-A breaker. How many PDU branches will you need to power the 12 servers?

__4__

6. What is the normal load (in kilowatts) of each UPS?

__25 kW__

7. What is the maximum load (in kilowatts) each UPS should be capable of handling?

__33 kW__

8. Will this be sufficient under normal conditions (both feeds active)?

__Yes__
_Correct! Each PSU is only 250 W._

9. Will this be sufficient (and conform to electrical code) if power feed A fails?

__No__
_Correct! Although it might not trip the breaker, running a 2,000-W load through a single branch (16 A × 208 V / 1.73 = 1,923-W limit) does not conform to code._
