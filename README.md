# Simulation of Ground Handling Operations based on Long Beach Airport
Code hosting for the second project for CSE 6730.  

## Contributed by: Jiahao Luo, Hyunjee Jin, Alicia Rossi, Sumana Sen

## Introduction
In modern days, there is increasing demands on the aircraft industry. Due to the high volume of air traffic demands, airports become congested and delays in the air traffic systems cause delays of flight operations in the airport and the congestions in airspace. Inherent delay uncertainty makes it difficult for airlines and air traffic service providers to manage passengers, fleets and crews efficiently. The unexpected delays also impact the passengers’ comfort level. In addition, increased congestion at busy airports results in significant financial and environmental inefficiencies.
<p>
In order to handle the high volume of demands for time and safety, a more efficient traffic management strategy is required to maintain current facilities. Reducing inefficiencies in ground space workflow can greatly reduce extra costs for airlines and airports as well as increasing passengers comfort by increasing the number of on-time flights.  Thus this project will focus on improving ground handling operations with the goal of increasing the number of on-time flights.  

## Problem Description
All ground handling work should be finished before aircraft departure. Therefore, the time needed to complete this work is integral to determining if a plane will have an ontime departure.  The ultimate purpose of this study is to maximize the total number of aircraft that departing on-time and minimize the total amount of cost for ground handlers. The quantification of the ground operation time for each aircraft would be calculated by organizing the ground handling work flow as parallel structure. For the simulation, we applied the ground handling work time for each work by aircraft type from Boeing and Airbus manuals. 
There are eight types of works for ground handling before departure: Catering, Cleaning, Fueling, Luggage loading, Maintenance, Boarding passengers, Water supply,  and Power supply.  We selected an airport in the USA and use the physical dimensions to base the travel time in our simulation. Also, the typical day’s flight schedule would be used to determine the time the interarrival time for flights.
<p>
There will be seven ground handling services for the ground handling hub, which are water supply, fuelling, power supply, catering, cleaning, baggage loading and maintenance. In most of the cases, the critical path should follow some specific the local causality constraint for example, aircraft bin cleaning should be done before passenger boarding. Also, according to the safety regulation, Passenger boarding cannot start while fueling is not finished. If there is malfunction with the aircraft, then maintenance will be required. And the total aircraft ground times depend on the establishment of the sequent execution of the events across all logical processes under local causality constraint.

## Interface
SimPy is a discrete-event simulation library. The behavior of active components (like vehicles, aircrafts or messages) is modeled with processes. All processes live in an environment. They interact with the environment and with each other via events. Processes are described by simple Python generators. They can be called process function or process method, depending on whether it is a normal function or method of a class. During their lifetime, they request resources and yield them in order to wait for them to be triggered. When a process yields an event, the process gets suspended. SimPy resumes the process, when the event occurs (we say that the event is triggered). Multiple processes can wait for the same event. When a resource is requested, if there is not a resource of that type available, SimPy adds that request to a priority queue.  Once the resource is available, the resource moves to the plane with the highest priority determined by the proximity to the departure time.   After using the event, the process is reactivated, and continues in the process.  
<p>
Our simulation environment consists of an airplane generator which then calls the other resources.  After it is generated, the airplane yields the process to the gate resource until it receives a gate.  Then it yields until all of the services are complete.  Once all of the services have been performed, control is then returned to the airplane process which simulates the plane taking off and then releases the gate resource for another plane.  




