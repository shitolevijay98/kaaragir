// src/App.js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function App() {
  const [labours, setLabours] = useState([]);
  const [name, setName] = useState('');
  const [skill, setSkill] = useState('');
  const [available, setAvailable] = useState(false);
  const [dailyIncome, setDailyIncome] = useState(0);

  useEffect(() => {
    axios.get('http://localhost:5000/labours')
      .then(response => setLabours(response.data))
      .catch(error => console.error('Error fetching data:', error));
  }, []);

  const addLabour = () => {
    axios.post('http://localhost:5000/labours', { name, skill, available, dailyIncome })
      .then(response => setLabours([...labours, response.data]))
      .catch(error => console.error('Error adding labour:', error));
  };

  return (
    <div>
      <h1>Karagir - Daily Labour Management</h1>
      <div>
        <input type="text" placeholder="Name" value={name} onChange={e => setName(e.target.value)} />
        <input type="text" placeholder="Skill" value={skill} onChange={e => setSkill(e.target.value)} />
        <input type="checkbox" checked={available} onChange={e => setAvailable(e.target.checked)} />
        <input type="number" placeholder="Daily Income" value={dailyIncome} onChange={e => setDailyIncome(e.target.value)} />
        <button onClick={addLabour}>Add Labour</button>
      </div>
      <ul>
        {labours.map(labour => (
          <li key={labour._id}>{labour.name} - {labour.skill} - {labour.available ? 'Available' : 'Not Available'} - ${labour.dailyIncome}</li>
        ))}
      </ul>
    </div>
  );
}

export default App;
