# Multi-UAV Mission Coordination System

A multi-drone search-and-rescue system developed for **NIDAR**, focused on coordinating unmanned aerial vehicles (UAVs) for aerial surveying, survivor identification, and mission-oriented operations.

The project combines **drone hardware engineering, geospatial mission planning, autonomous systems, computer vision, and ground-control software** into a modular system designed to support coordinated operations.

> **Project status:** Active development · NIDAR competition 2026–27

## Project Overview

Search-and-rescue missions require reliable coordination between aerial vehicles, geographic mission data, onboard sensing, and ground operators. This project aims to bring these capabilities together through a shared mission architecture connecting the physical drone platform with its software systems.

The system is being developed across three interconnected areas:

- **Hardware and system engineering:** Computing architecture, electronic system design, component selection, mechanical validation, and procurement planning.
- **Mission planning and autonomy:** Geographic boundary processing, waypoint generation, survey planning, delivery-route generation, and ROS 2-based system interfaces.
- **Ground Control Station (GCS) and perception:** A web-based operator interface for mission configuration, multi-drone visualization, telemetry, camera feeds, and detection data.

## Technical Architecture

The system follows a modular architecture that separates operator interaction, mission logic, geographic processing, vehicle communication, and perception.

```text
                 Ground Control Station
                  React + TypeScript
                          |
                       ROSBridge
                          |
                        ROS 2
                          |
          +---------------+---------------+
          |               |               |
     Mission Planning   Telemetry       Perception
     & Geospatial       & Commands      & Detections
          |               |               |
          +---------------+---------------+
                          |
                 Drone / Flight Systems
```

*Architecture overview. The diagram represents the intended system structure; individual integrations are being validated incrementally.*

## Engineering Contributions

### Ground Control Station

- Developed a component-based interface using React and TypeScript for mission configuration, drone status, and geographic visualization.
- Implemented a MapLibre-based map interface for mission boundaries, assigned drone routes, waypoints, and vehicle markers.
- Established ROSBridge communication between the web interface and ROS 2, with initial telemetry and mission-action paths verified.
- Developed a reusable flight HUD and published it as an independent open-source React component.

### Mission Planning and Geospatial Processing

- Developed ROS 2/Python components for survey planning, geographic processing, and delivery-route generation.
- Structured mission data and custom ROS interfaces for boundaries, waypoints, drone state, and delivery routes.
- Designed modular service and action interfaces to separate mission preparation from mission execution.

### Hardware and System Engineering

- Evaluated onboard computing architectures against computer-vision workloads, power, weight, software compatibility, and integration constraints.
- Created electronic system diagrams and established bill-of-materials and budget-tracking workflows.
- Participated in mechanical design exploration and flight testing, using observed failure modes to inform reliability and validation priorities.

### Computer Vision Infrastructure

- Worked on the NVIDIA-based training and inference environment for the project's RT-DETR perception pipeline.
- Designed structured detection messages intended to associate detection results with drone position, altitude, and timestamps.
- Investigated deployment and integration requirements for connecting perception outputs with the broader ROS 2 system.

## Technology Stack

| Area | Technologies |
|---|---|
| Ground Control Station | React, TypeScript, MapLibre GL JS |
| Robotics Middleware | ROS 2, ROSBridge |
| Backend and Planning | Python, ROS 2 services and actions |
| Geospatial Processing | Geographic coordinates, KML, GeoJSON, Shapely, PyProj |
| Computer Vision | NVIDIA TAO Toolkit, RT-DETR, ONNX, TensorRT exploration |
| Flight Systems | MAVROS/PX4 integration exploration |
| Hardware Engineering | SolidWorks, system diagrams, component and power/weight evaluation |

## Project Status and Validation

The project is progressing from individual subsystem development toward a more integrated system.

**Implemented foundations**
- Modular GCS architecture and multi-drone map visualization.
- Geographic mission-data processing and route-planning components.
- ROS 2 interfaces for mission operations and vehicle data.
- A reusable, publicly published drone HUD component.

**Ongoing work**
- Expanding and validating telemetry, command, and mission-action interfaces.
- Integrating perception data into operator-facing workflows.
- Continuing hardware validation and system-level integration.

The full autonomous mission workflow, including reliable coordination with physical flight hardware, remains under development. Individual software components and verified integration paths should not be interpreted as proof of complete autonomous flight readiness.

## Open Source

A reusable flight HUD developed during this project is available independently:

- **Repository:** [react-drone-hud](https://github.com/gideon-jacob/react-drone-hud)
- **npm package:** [`@gideonjacob/react-drone-hud`](https://www.npmjs.com/package/@gideonjacob/react-drone-hud)
- **Live demo:** [View the HUD](https://gideon-jacob.github.io/react-drone-hud/)

Publishing the HUD separately allows other developers to reuse the component without depending on the full drone-system codebase.

## About the Project

This is an ongoing engineering project developed for NIDAR 2026–27. Its development involves iterative architecture decisions, subsystem implementation, integration testing, and practical hardware validation.

The source repository is private while the competition is in progress. This README provides a high-level overview without disclosing competition-sensitive implementation details.
