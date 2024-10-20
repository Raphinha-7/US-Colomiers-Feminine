# Senior Féminine U.S Colomiers Saison 24/25
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Statistiques des Joueurs</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 0;
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
    </style>
</head>
<body>
    <h1>Statistiques des Joueuse</h1>
    <table id="stats-table">
        <thead>
            <tr>
                <th>Nom</th>
                <th>Prénom</th>
                <th>Matchs Joués</th>
                <th>Buts Marqués</th>
                <th>Passes Décisives</th>
            </tr>
        </thead>
        <tbody></tbody>
    </table>

    <script>
        fetch('http://localhost:3000/api/statistiques')
            .then(response => response.json())
            .then(data => {
                const tableBody = document.getElementById('stats-table').getElementsByTagName('tbody')[0];
                data.forEach(player => {
                    const row = tableBody.insertRow();
                    row.insertCell(0).textContent = player.Nom;
                    row.insertCell(1).textContent = player.Prénom;
                    row.insertCell(2).textContent = player.Matchs_joués;
                    row.insertCell(3).textContent = player.Buts_marques;
                    row.insertCell(4).textContent = player.Passes_decisives;
                });
            })
            .catch(error => console.error('Erreur:', error));
    </script>
</body>
</html>
