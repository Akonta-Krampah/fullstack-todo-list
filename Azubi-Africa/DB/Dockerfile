const express = require('express');
const mysql = require('mysql2');
const app = express();
const port = 5000;

const db = mysql.createConnection({
  host: process.env.DB_HOST || 'db',
  user: 'root',
  password: process.env.DB_PASSWORD || 'example',
  database: process.env.DB_NAME || 'testdb'
});

app.get('/health', (req, res) => res.send('Backend is running'));
app.get('/db-check', (req, res) => {
  db.query('SELECT 1', (err, result) => {
    if (err) return res.status(500).send('DB error');
    res.send('DB OK');
  });
});

app.listen(port, () => console.log(`Backend running on port ${port}`));

