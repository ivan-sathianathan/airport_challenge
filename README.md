#Airport challenge

This is my solution to the first weekend challenge we were set at Makers Academy. We had to fulfil the following user stories:

```
As an air traffic controller
So planes can land safely at my airport
I would like to instruct a plane to land

As an air traffic controller
So planes can take off safely from my airport
I would like to instruct a plane to take off

As an air traffic controller
So that I can avoid collisions
I want to prevent airplanes landing when my airport if full

As an air traffic controller
So that I can avoid accidents
I want to prevent airplanes landing or taking off when the weather is stormy

As an air traffic controller
So that I can ensure safe take off procedures
I want planes only to take off from the airport they are at

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller
So the system is consistent and correctly reports plane status and location
I want to ensure a flying plane cannot take off and cannot be in an airport

As an air traffic controller
So the system is consistent and correctly reports plane status and location
I want to ensure a plane that is not flying cannot land and must be in an airport

As an air traffic controller
So the system is consistent and correctly reports plane status and location
I want to ensure a plane that has taken off from an airport is no longer in that airport
```

#Usage

To run this project, perform the following Steps

1. Clone this repo
2. Run ```bundle```
3. Instantiate a Weather Reporter and pass this to a new Airport
  ```
  weather_reporter = WeatherReporter.new
  airport = Airport.new(weather_reporter)
  ```
4. Instantiate a new Plane object. This plane will already be flying so ask the airport to land this plane
  ```
  plane = Plane.new
  airport.land(plane)
  ```
5. Ask the airport to take off the plane. This will happen depending on whether the weather reporter determines it to be stormy or not.

  ```
  airport.take_off(plane)
  ```
More documentation on the behaviour of each class and their methods can be found by running ```rspec```

```
Airport
  #land
    when not stormy
      instructs a plane to land
      when full
        raises an error
    when stormy
      raises an error
  #take_off
    when not stormy
      instructs a plane to take off
      returns the plane that took off
      raises an error if plane is not at this airport
    when stormy
      raises an error
  #planes
    returns planes that are at the airport
    does not return planes that have taken off
  defaults
    has a default capacity

User Stories
  when not stormy
    so planes land at airport, instruct a plane to land
    so planes take off from airport, instruct a plane to take off
    takes off planes only from the airport they are at
    flying planes cannot take off
    flying planes cannot be in an airport
    taking off a plane removes it from that airport
    landed planes cannot land
    landed planes must be in an airport
    airports have a default capacity
    when airport full
      does not allow planes to land
  when weather is stormy
    does not allow planes to land
    does not allow planes to take off

Plane
  #take_off
    should respond to #take_off
    raises an error if already flying
  #land
    stores the airport the plane landed at
    raises an error if already landed
  #airport
    should respond to #airport
    raises an error if already flying

WeatherReporter
  #stormy?
    can be non-stormy
    can be stormy
```
