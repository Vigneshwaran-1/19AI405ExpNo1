<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: VIGNESHWARAN P</h3>
<h3>Register Number: 212224040358</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>

# Program

    
    import random
    class HospitalEnvironment:
    def __init__(self, num_rooms=2):
        
        self.rooms = [round(random.uniform(97.0, 102.0), 1) for _ in range(num_rooms)]
        self.num_rooms = num_rooms

    def get_patient_temperature(self, room_id):
        return self.rooms[room_id]

    def update_patient(self, room_id):
        """After treatment, patient becomes healthy (reset temperature)."""
        self.rooms[room_id] = round(random.uniform(97.0, 98.5), 1)
    class MedicineAgent:
    def __init__(self, environment):
        self.env = environment
        self.current_room = 0
        self.performance = 0

    def check_and_treat(self):
        temp = self.env.get_patient_temperature(self.current_room)
        if temp > 98.5:
            print(f"Room {self.current_room}: Patient has fever ({temp}°F). Prescribing medicine...")
            self.performance += 1
            self.env.update_patient(self.current_room)
        else:
            print(f"Room {self.current_room}: Patient is healthy ({temp}°F). No medicine needed.")

    def move(self):
        self.current_room = (self.current_room + 1) % self.env.num_rooms
        self.performance -= 1
        print(f"Agent moved to Room {self.current_room}. Performance decreased.")

    def run(self, steps=6):
        for step in range(steps):
            print(f"\nStep {step+1}:")
            self.check_and_treat()
            self.move()
        print("\nFinal Performance:", self.performance)
    hospital = HospitalEnvironment(num_rooms=2)
    agent = MedicineAgent(hospital)
    agent.run(steps=4)


# Output

<img width="449" height="350" alt="image" src="https://github.com/user-attachments/assets/bb350240-e18d-4c79-9647-7efe546f909d" />

# Result 
Thus given experiment is done successfully. 
