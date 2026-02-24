# Lab 22: Building Timelines for Investigations

## Objectives
- Understand the concept and importance of timelines in investigations.
- Learn how to create, organize, and analyze timelines using open-source tools.
- Develop skills in adding and tagging events with notes for better insights.

## Prerequisites
- Basic understanding of investigative processes and digital forensics.
- Familiarity with open-source tools and terminal commands.
- Access to a computer with necessary tools installed (e.g., TimelineJS).

## Introduction
In digital investigations, timelines are crucial for visualizing sequences of events, understanding patterns, and gaining insights into incidents. This lab demonstrates how to create and manage timelines using free, open-source tools.

---

## Lab Tasks

### Task 1: Set Up Your Environment

#### Step 1.1: Install TimelineJS

Open your terminal.

Update your package manager:
```bash
sudo apt-get update

Install Node.js and npm:

sudo apt-get install nodejs npm

Install TimelineJS:

npm install -g timelinejs
Step 1.2: Verify the Installation
timeline --version
Task 2: Create a New Timeline
Step 2.1: Initialize a New Timeline Project
mkdir investigation_timeline && cd investigation_timeline
Step 2.2: Create a Timeline
timeline create
Task 3: Add Events to the Timeline
Step 3.1: Define Events

Example event structure:

- date: "2023-10-01"
  title: "Unauthorized Login Attempt"
  description: "Login attempt from suspicious IP address."
Step 3.2: Add Events to Your Timeline

Open the timeline data file (e.g., timeline.json) in a text editor and insert event data.

Step 3.3: Save Your Timeline

Save the updated file to apply changes.

Task 4: Organize and Enhance Your Timeline
Step 4.1: Add Notes and Tags

Example with tags and notes:

- date: "2023-10-01"
  title: "Unauthorized Login Attempt"
  description: "Login attempt from suspicious IP address."
  tags: ["suspicious", "critical"]
  notes: "Occurred post software update, requires further investigation."
Step 4.2: Visualize the Timeline
timeline serve

Open the rendered timeline in your web browser to analyze the sequence and event details.

Case Study Example

If a corporation experiences a data breach, constructing a detailed timeline of login attempts and network activity can help identify suspicious access patterns and trace the potential source of compromise.

Conclusion

What I have learned: created and managed investigation timelines using open-source tools, organized events with notes and tags, and visualized event sequences to support digital forensic investigations.
