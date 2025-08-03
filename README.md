// Game for Promzy and Chi Berry // Multiplayer riddle + mini games (React + Vite style)

// --- src/App.jsx --- import { useState, useEffect } from 'react'; import './App.css';

const riddles = [ { question: "You see a boat filled with people. It hasn't sunk, but when you look again, you don't see a single person on board. Why?", answer: "They were all married" }, { question: "I am not alive, but I can grow. I don't have lungs, but I need air. I don't have a mouth, but water kills me. What am I?", answer: "Fire" }, { question: "You usually draw the thing. It's cheating. What is it?", answer: "Life" } ];

function App() { const [playerName, setPlayerName] = useState(''); const [started, setStarted] = useState(false); const [index, setIndex] = useState(0); const [input, setInput] = useState(''); const [message, setMessage] = useState('');

const current = riddles[index];

const handleSubmit = () => { if (input.trim().toLowerCase() === current.answer.toLowerCase()) { setMessage('✅ Correct!'); setTimeout(() => { setIndex(i => (i + 1) % riddles.length); setInput(''); setMessage(''); }, 1000); } else { setMessage('❌ Try again'); } };

if (!started) { return ( <div className="screen"> <h2>Welcome to Brain Duel Arena 🧠</h2> <input placeholder="Enter your name" value={playerName} onChange={e => setPlayerName(e.target.value)} /> <button onClick={() => setStarted(true)}>Start Game</button> </div> ); }

return ( <div className="screen"> <h2>Hello, {playerName || 'Player'} 👋</h2> <h3>Riddle:</h3> <p>{current.question}</p> <input placeholder="Type your answer..." value={input} onChange={e => setInput(e.target.value)} /> <button onClick={handleSubmit}>Submit</button> <p>{message}</p> </div> ); }

export default App;

// --- src/main.jsx --- import React from 'react'; import ReactDOM from 'react-dom/client'; import App from './App'; import './index.css';

ReactDOM.createRoot(document.getElementById('root')).render( <React.StrictMode> <App /> </React.StrictMode> );

// --- index.html ---

<!DOCTYPE html><html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Brain Duel Arena</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>// --- package.json --- { "name": "brain-duel-arena", "version": "1.0.0", "scripts": { "dev": "vite", "build": "vite build", "preview": "vite preview" }, "dependencies": { "react": "^18.2.0", "react-dom": "^18.2.0" }, "devDependencies": { "vite": "^4.0.0" } }

// --- index.css --- body { font-family: Arial, sans-serif; background: #fefae0; color: #333; padding: 20px; } .screen { max-width: 500px; margin: auto; text-align: center; } input { padding: 10px; margin: 10px 0; width: 80%; font-size: 1em; } button { padding: 10px 20px; background: #ffb703; color:

