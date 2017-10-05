ics_production - deployment repository
======

This repository is to store all physical deployment information for PFS ICS, 
such as unit registration for racks, ports of network switches, etc., and 
all configurations SHALL be registered into this repository in a format 
defined in `YAML file format`_ section.


YAML file format
======

All registration files SHALL be placed as a file in 'data' directory written 
in YAML format and be written in following organization. 

- Top level SHALL be a mapping consisted of "device" and "assign"
- "device" of top level mapping contains device information and is organized as mapping, with contents as followings (all required otherwise noted):

  - name: Machine readable name, this SHALL be hostname if device has.
  - place: Place where the device is located
  - units: Maximum number of units (or ports), the device provides
  - class: Device class, from "switch", "rack", "pdu", "kvm"
  - description: Human readable description of the device

- "assign" of top level mapping contains unit registrations and is organized as sequence of mappings, with contents of each mapping as followings (all required otherwise noted):

  - id: Numerical ID of unit or port
  - name: Name of connected, port name (hostname + port ID charactor) of connected target
  - hostname: Hostname of connected target
  - port: (optional) Port ID in the hostname
  - description: (optional) Human readable description of connected target

