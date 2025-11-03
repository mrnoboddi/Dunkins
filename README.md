OPENWORLD-CHAT/frontend/src/App.tsx
code file:
"                                           // frontend/src/App.tsx
import React, { useState, useEffect } from 'react';
import { BrowserRouter as Router, Routes, Route, Navigate } from 'react-router-dom';
import Login from './pages/Login';
import Chat from './pages/Chat';
import Profile from './pages/Profile';
import { Signup } from './pages/Signup';
import './App.css';

export default function App() {
  const [token, setToken] = useState<string | null>(localStorage.getItem('access'));

  // 🧹 Optional: Clear tokens on load (for dev/testing)
  useEffect(() => {
    // Uncomment the lines below if you want to reset auth every time app reloads
    // localStorage.removeItem('access');
    // localStorage.removeItem('refreshToken');
  }, []);

  const handleAuth = (newToken: string) => {
    setToken(newToken);
    localStorage.setItem('access', newToken);
  };

  return (
    <Router>
      <div style={{ padding: 20, textAlign: 'center' }}>
        <h1>Welcome to OpenWorld Chat</h1>

        {token ? (
          <>
            <p style={{ color: 'green' }}>✅ You’re logged in!</p>
            <Routes>
              <Route path="/profile" element={<Profile />} />
              <Route path="/chat" element={<Chat token={token} />} />
              <Route path="*" element={<Navigate to="/chat" />} />
            </Routes>
          </>
        ) : (
          <>
            <p style={{ marginBottom: 10 }}>Please log in or sign up to continue.</p>
            <Routes>
              <Route path="/" element={<Login onAuth={handleAuth} />} />
              <Route path="/signup" element={<Signup />} />
              <Route path="*" element={<Navigate to="/" />} />
            </Routes>
          </>
        )}
      </div>
    </Router>
  );
}                                          ".

Errors to fix: 
" 1.
[{
	"resource": "/c:/Users/Pinias/openworld-chat/frontend/src/App.tsx",
	"owner": "typescript",
	"code": "2614",
	"severity": 8,
	"message": "Module '\"./pages/Signup\"' has no exported member 'Signup'. Did you mean to use 'import Signup from \"./pages/Signup\"' instead?",
	"source": "ts",
	"startLineNumber": 7,
	"startColumn": 10,
	"endLineNumber": 7,
	"endColumn": 16,
	"origin": "extHost1"
}]

2.
 [{
	"resource": "/c:/Users/Pinias/openworld-chat/frontend/src/App.tsx",
	"owner": "typescript",
	"code": "2322",
	"severity": 8,
	"message": "Type '{ onAuth: (newToken: string) => void; }' is not assignable to type 'IntrinsicAttributes'.\n  Property 'onAuth' does not exist on type 'IntrinsicAttributes'.",
	"source": "ts",
	"startLineNumber": 43,
	"startColumn": 47,
	"endLineNumber": 43,
	"endColumn": 53,
	"origin": "extHost1"
}].

3.[{
	"resource": "/c:/Users/Pinias/openworld-chat/frontend/src/App.tsx",
	"owner": "typescript",
	"code": "6133",
	"severity": 4,
	"message": "'React' is declared but its value is never read.",
	"source": "ts",
	"startLineNumber": 2,
	"startColumn": 8,
	"endLineNumber": 2,
	"endColumn": 13,
	"tags": [
		1
	],
	"origin": "extHost1"
}]
