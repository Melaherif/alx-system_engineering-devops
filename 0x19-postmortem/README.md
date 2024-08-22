# Postmortem: Outage on Web Service

## Issue Summary
- **Duration:** August 22, 2024, 2:00 PM - 4:30 PM UTC+2
- **Impact:** 60% of users experienced slow loading times on the website. Affected pages took up to 30 seconds to load.
- **Root Cause:** The issue was caused by a memory leak in the backend service that handles database queries.

## Timeline
- **2:00 PM:** Monitoring system alerted high response times.
- **2:05 PM:** Engineer on call verified the issue and escalated it.
- **2:10 PM:** Investigated the database server for slow queries.
- **2:30 PM:** Misleading assumption that a specific query was causing the issue.
- **3:00 PM:** Discovered that the memory usage was abnormally high on the backend service.
- **3:30 PM:** Identified the memory leak in a specific function handling data aggregation.
- **4:00 PM:** Deployed a fix and monitored the results.
- **4:30 PM:** Issue fully resolved, and service restored to normal.

## Root Cause and Resolution
- **Root Cause:** The memory leak was due to improper handling of large data sets in the backend service. The data aggregation function did not release resources correctly after processing, leading to increased memory usage over time.
- **Resolution:** Refactored the aggregation function to properly release memory and optimized the code for handling large data sets.

## Corrective and Preventative Measures
- Improve monitoring on memory usage for all backend services.
- Refactor other critical functions to ensure proper resource management.
- Conduct code reviews focused on resource handling and optimization.
- Add automated tests to simulate large data loads and catch potential memory leaks.


