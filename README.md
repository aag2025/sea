# sea
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crypto Communities</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .community {
            margin-bottom: 10px;
        }
    </style>
</head>
<body>
    <h1>Crypto Communities</h1>
    <div id="communities"></div>
    <h2>Add a new community</h2>
    <form id="communityForm">
        <input type="text" id="name" placeholder="Name" required>
        <input type="text" id="description" placeholder="Description">
        <button type="submit">Add Community</button>
    </form>
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            fetch('/communities')
                .then(response => response.json())
                .then(data => {
                    const communitiesDiv = document.getElementById('communities');
                    data.forEach(community => {
                        const div = document.createElement('div');
                        div.className = 'community';
                        div.innerHTML = `<strong>${community.name}</strong>: ${community.description}`;
                        communitiesDiv.appendChild(div);
                    });
                });

            document.getElementById('communityForm').addEventListener('submit', function(event) {
                event.preventDefault();
                const name = document.getElementById('name').value;
                const description = document.getElementById('description').value;

                fetch('/community', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({ name, description })
                })
                .then(response => response.json())
                .then(message => {
                    alert(message.message);
                    window.location.reload();
                });
            });
        });
    </script>
</body>
</html>
 document.getElementById('communityForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const description = document.getElementById('description').value;

            fetch('/community', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({ name, description })
            })
            .then(response => response.json())
            .then(message => {
                alert(message.message);
                window.location.reload();
            });
        });
    });
</script>
