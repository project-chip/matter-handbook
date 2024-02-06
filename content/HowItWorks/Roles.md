+++
title = "Roles"
chapter = false
weight = 5
+++
An important note is that while these definitions explain the distinct roles as defined in the Matter specification, in many cases, the products in users’ homes have the ability to take on different roles or serve in multiple roles at once.

## Matter Device
A smart home hardware product that supports Matter, so that it can be connected to and controlled by a Matter Controller. Examples: light bulbs, switches, sensors, thermostats, blinds, door locks, bridges, and media devices.

## Matter Fabric
Matter Devices are connected together on a virtual network within the home called a Matter Fabric, a private virtual network over which Matter Devices, Admins, and Controllers communicate with each other. Matter Fabrics can span across the Wi-Fi, Thread, and Ethernet physical networks within the home. Matter Devices can be connected to one or more Fabrics at a time, each managed by a Matter Administrator. Sometimes Matter Fabrics are referred to as “services” by smart home apps and platforms.

## Matter Commissioner
A device or application that is used as a tool to set up a Matter Device, in other words bring it into a Matter Fabric. Commissioners first verify the device’s authenticity and then assign network credentials as needed. A platform, device vendor, or other Matter-enabled app, mobile OS, smart speaker, or display may all provide a Matter Commissioner. A Commissioner can be an independent tool or part of a device or system that includes other roles such as Administrator or Controller.

## Matter Administrator
A device or application that creates, maintains, and manages security and privileges for all devices on the Fabric it administers. Administrators can be a physical device like a hub or software like an app. Matter’s Multi-Admin feature which allows Devices to connect to multiple smart home platforms simultaneously, is a reference to connecting Devices to multiple Matter Administrators, and thus to multiple Fabrics.

## Matter Controller
As the name suggests, a Matter Controller is an entity that can control Matter devices the user has connected to it. Matter Controller functionality can be built into many types of hardware devices like phones, always-powered smart home hubs that provide local and remote control, smart switches and buttons, or even mobile apps. There can be multiple Matter Controllers on a Fabric to provide redundancy and/or convenient controls for users. 

It’s important to note that in most cases, a Matter Controller is exclusive to the company that provides it. For instance, a smart speaker with a Matter Controller from Smart Home Platform A can be used to control Matter devices through the Platform A app, voice control, or other interfaces. But if you want to use Platform B to control Matter devices, you’ll need to have one of Platform B’s Controllers. An exception to this is devices such as switches, buttons, sensors, etc that can be commissioned as third-party Controllers onto a Fabric.

With Matter’s Multi-Admin features, you can connect Matter devices to multiple platforms if you have a Matter Controller for each platform in your home. 

Matter Controller is the technical term for this role, though note that many smart home platforms colloquially refer to their devices that contain Matter Controllers as “hubs” (see below).

## Matter Bridge
A Matter Bridge translates from one protocol to another, allowing non-Matter smart home devices (such as those using Zigbee or Z-Wave) to connect to a Matter Fabric via the Bridge. This allows consumers to use their non-Matter smart home devices along with their new Matter devices to continue growing their unified smart home.

A Matter Bridge is a different role than a Controller. A bridge serves as an intermediary for Matter and non-Matter devices. However, Bridges may be built into a number of devices like smart home “hubs” that also serve as Matter Controllers. For a deeper dive read Why Bridging Matters. 


_This content was first published on the Alliance website as a blog_
