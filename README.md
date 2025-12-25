This repository contains a Distributed Systems coursework project implemented using gRPC in Java.

The system simulates multiple smart devices communicating over different gRPC interaction patterns, including Unary,
Client Streaming, Server Streaming, and Bidirectional Streaming.

The project also demonstrates:
- Service discovery using jmDNS
- Remote error handling
- Metadata-based authorization
- Deadlines and stream cancellation
- A Java Graphical User Interface (GUI) for interaction

The system consists of four independent gRPC services, each simulating a real-world smart device scenario:
1. Smart Car:	Unary,	Accident alert system
2. Smart Watch:	Client Streaming	Step tracking & activity summary
3. Mobile App:	Server Streaming	Hydration reminder system
4. Heart Monitor:	Bidirectional Streaming	Real-time heart rate monitoring
All services are discoverable on the local network using jmDNS.

Services Description:
1️. Smart Car – Unary Service
Simulates a smart car accident alert system.
Client sends accident severity and location
Server responds with an alert message
Includes remote error handling for invalid input (empty status)
Service Type: Unary RPC

2. Smart Watch – Client Streaming
Simulates a smartwatch step-tracking system.
Client streams step data every few seconds
Server calculates: Total steps, Calories burned, Active time, Personalized feedback
Uses metadata authentication via client-id
Unauthorized clients are rejected
Service Type: Client Streaming

3. Mobile App – Server Streaming
Simulates a hydration reminder application.
Client sends one request
Server streams multiple reminders over time
Client uses gRPC deadlines to handle slow servers
Supports simulated delays for testing
Service Type: Server Streaming

4. Heart Monitor – Bidirectional Streaming
Simulates real-time heart rate monitoring.
Client continuously sends BPM values
Server responds with immediate feedback
Client can cancel the stream via GUI
Server handles stream cancellation gracefully
Service Type: Bidirectional Streaming

All services are registered and discovered automatically using jmDNS:
_smartCar._tcp.local.
_smartWatch._tcp.local.
_mobileApp._tcp.local.
_heartMonitor._tcp.local.
This allows clients to dynamically locate servers without hardcoded IPs.

Graphical User Interface (GUI)
The project includes a Java Swing GUI with four tabs:
1. Smart Car GUI
Send accident alerts
Simulate invalid input
2. Smart Watch GUI
Start streaming steps
Toggle valid/invalid client IDs
3. Mobile App GUI
Set reminder intervals
Simulate server delays
4. Heart Monitor GUI
Start/stop bidirectional streaming
Cancel stream manually

Main entry point: MainApp.java
How to Run:
Start a server for the desired service
Start the corresponding client (via GUI or IDE)
Services are discovered automatically using jmDNS
Interact with services using the GUI controls

Technologies Used:
Java
gRPC
Protocol Buffers
jmDNS
Java Swing (GUI)
