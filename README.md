<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kirim Laporan Jalan Rusak</title>
    <style>
        /* Reset dan font */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #333;
            overflow-x: hidden;
            animation: fadeIn 1s ease-in;
            /* Background gradien biru mewah dengan animasi */
            background: linear-gradient(-45deg, #0f4c75, #3282b8, #bbe1fa, #1b262c);
            background-size: 400% 400%;
            animation: gradientShift 10s ease infinite;
        }
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            max-width: 600px;
            margin: 50px auto;
            background: #fff;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            padding: 30px;
            animation: slideUp 0.8s ease-out;
            transition: box-shadow 0.5s ease; /* Interaktif saat hover */
        }
        .container:hover {
            box-shadow: 0 15px 40px rgba(0, 0, 0, 0.3); /* Lebih dramatis saat hover */
        }
        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        .logo {
            width: 200px;
            height: 200px;
            margin: 0 auto 30px;
            display: block;
            animation: bounceIn 1s ease-out;
        }
        h1 {
            text-align: center;
            color: #4a4a4a;
            margin-bottom: 20px;
            font-size: 2.5em;
            animation: bounceIn 1s ease-out;
        }
        @keyframes bounceIn {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.05); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        form {
            display: flex;
            flex-direction: column;
        }
        label {
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }
        input, textarea {
            padding: 12px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 1em;
            transition: border-color 0.3s, box-shadow 0.3s;
        }
        input:focus, textarea:focus {
            border-color: #3282b8;
            box-shadow: 0 0 10px rgba(50, 130, 184, 0.3);
            outline: none;
        }
        textarea {
            resize: vertical;
            min-height: 100px;
        }

        button {
            padding: 15px;
            background: linear-gradient(135deg, #3282b8, #0f4c75);
            color: #fff;
            border: none;
            border-radius: 8px;
            font-size: 1.2em;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s, background 0.3s;
            animation: pulse 2s infinite;
        }
        button:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            background: linear-gradient(135deg, #0f4c75, #3282b8); /* Gradien terbalik saat hover */
        }
        @keyframes pulse {
            0% { box-shadow: 0 0 0 0 rgba(50, 130, 184, 0.7); }
            70% { box-shadow: 0 0 0 10px rgba(50, 130, 184, 0); }
            100% { box-shadow: 0 0 0 0 rgba(50, 130, 184, 0); }
        }

        @media (max-width: 768px) {
            .container {
                margin: 20px;
                padding: 20px;
            }
            h1 {
                font-size: 2em;
            }
            .logo {
                width: 60px;
                height: 60px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="smk-negeri-2-kota-mojokerto-public-vocational-high-school-2-malang-vocational-school-education-png-favpng-SifsuretwGhtRNsk2aqRXzh11-removebg-preview.png" alt="Logo SMK Negeri 2 Mojokerto" class="logo">
        <h1>Kirim Laporan Jalan Rusak</h1>
        <form id="reportForm">
            <label for="location">Lokasi Jalan Rusak:</label>
            <input type="text" id="location" placeholder="Masukkan lokasi" required>

            <label for="description">Deskripsi Kerusakan Jalan:</label>
            <textarea id="description" placeholder="Jelaskan kondisi jalan rusak..." required></textarea>

            <label for="photo">Upload Foto Jalan yang Rusak:</label>
            <input type="file" id="photo" accept="image/*">

            <button type="submit">Kirim Laporan</button>
        </form>
    </div>

    <script>
        document.getElementById('reportForm').addEventListener('submit', function(event) {
            event.preventDefault();

            // Ambil data dari form
            const location = document.getElementById('location').value;
            const description = document.getElementById('description').value;
            const photoInput = document.getElementById('photo');
            let photo = null;

            // Jika ada foto, buat URL untuk preview (simulasi)
            if (photoInput.files[0]) {
                photo = URL.createObjectURL(photoInput.files[0]);
            }

            // Simpan ke localStorage
            const reports = JSON.parse(localStorage.getItem('roadReports')) || [];
            reports.push({ location, description, photo });
            localStorage.setItem('roadReports', JSON.stringify(reports));

            alert('Laporan berhasil dikirim!');
            // Redirect ke dashboard
            window.location.href = 'laporanberhasil.html';
        });
    </script>
</body>
</html>
