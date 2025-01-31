# league
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Football League Table</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #121212;
            text-align: center;
            margin: 0;
            padding: 0;
            color: white;
        }
        table {
            width: 90%;
            margin: 20px auto;
            border-collapse: collapse;
            background: #1e1e1e;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            color: white;
        }
        th, td {
            padding: 12px;
            border: 1px solid #333;
            text-align: center;
        }
        th {
            background: #37003c;
            color: white;
            text-transform: uppercase;
        }
        tr:nth-child(even) {
            background: #2a2a2a;
        }
        tr:hover {
            background: #444;
        }
        h1 {
            background: #37003c;
            color: white;
            padding: 15px;
            margin: 0;
        }
        .form-cell {
            display: flex;
            justify-content: center;
            gap: 5px;
        }
    </style>
</head>
<body>
    <h1>Premier League Table</h1>
    <table>
        <thead>
            <tr>
                <th>Position</th>
                <th>Team</th>
                <th>Played</th>
                <th>Won</th>
                <th>Drawn</th>
                <th>Lost</th>
                <th>Goals</th>
                <th>Points</th>
                <th>Form</th>
            </tr>
        </thead>
        <tbody id="league-table">
        </tbody>
    </table>

    <script>
        let teams = [
            { name: "Hammasi", played: 1, won: 0, drawn: 0, lost: 1, goals: 0, points: 0, form: ["❌"] },
            { name: "Ammar", played: 2, won: 2, drawn: 0, lost: 0, goals: 5, points: 6, form: ["✅", "✅"] },
            { name: "Ahlasi", played: 1, won: 0, drawn: 0, lost: 1, goals: 0, points: 0, form: ["❌"] },
            { name: "Saifi", played: 0, won: 0, drawn: 0, lost: 0, goals: 0, points: 0, form: [] }
        ];

        function updateTable() {
            teams.sort((a, b) => b.points - a.points || b.goals - a.goals);
            let tableBody = document.getElementById("league-table");
            tableBody.innerHTML = "";
            
            teams.forEach((team, index) => {
                let row = <tr>
                    <td>${index + 1}</td>
                    <td>${team.name}</td>
                    <td>${team.played}</td>
                    <td>${team.won}</td>
                    <td>${team.drawn}</td>
                    <td>${team.lost}</td>
                    <td>${team.goals}</td>
                    <td>${team.points}</td>
                    <td class="form-cell">${team.form.slice(-5).join(" ")}</td>
                </tr>;
                tableBody.innerHTML += row;
            });
        }

        updateTable();
    </script>
</body>
</html>
