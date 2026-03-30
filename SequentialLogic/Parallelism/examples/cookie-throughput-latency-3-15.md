## Cookie Production Problem

Ben Bitdiddle is throwing a milk and cookies party to celebrate the installation of his traffic light controller. It takes him 5 minutes to roll cookies and place them on his tray. It then takes 15 minutes for the cookies to bake in the oven. Once the cookies are baked, he starts another tray. What is Ben's throughput and latency for a tray of cookies?

### Solution:

In this example a tray of cookies is a token. The **latency** is 20 minutes (or 1/3 hour) per tray. The **throughput** is 3 trays/hour.

**Explanation:**
- **Latency** = total time from start to finish for one tray = 5 minutes (rolling) + 15 minutes (baking) = 20 minutes = 1/3 hour per tray
- **Throughput** = rate at which trays are completed = 1 tray per 20 minutes = 3 trays per hour
