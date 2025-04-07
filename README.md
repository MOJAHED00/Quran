
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <title>البحث عن آية</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f0f0;
            padding: 20px;
            text-align: right;
        }
        input, button {
            padding: 10px;
            margin-top: 10px;
            width: 90%;
            font-size: 16px;
        }
        #results {
            margin-top: 20px;
            background: white;
            padding: 15px;
            border-radius: 8px;
        }
        h2 {
            color: #2c3e50;
        }
    </style>
</head>
<body>
    <h2>البحث عن آية</h2>
    <input type="text" id="searchInput" placeholder="اكتب كلمة أو جزء من آية">
    <button onclick="searchAyah()">ابحث</button>
    <div id="results"></div>

    <script>
        const ayat = [
            { text: "الحمد لله رب العالمين", surah: "الفاتحة", number: 2 },
            { text: "الله لا إله إلا هو الحي القيوم", surah: "البقرة", number: 255 },
            { text: "قل هو الله أحد", surah: "الإخلاص", number: 1 },
            { text: "إن مع العسر يسرا", surah: "الشرح", number: 6 },
            { text: "ولسوف يعطيك ربك فترضى", surah: "الضحى", number: 5 },
            { text: "إنا أعطيناك الكوثر", surah: "الكوثر", number: 1 },
            { text: "رب اشرح لي صدري", surah: "طه", number: 25 }
        ];

        function searchAyah() {
            let query = document.getElementById("searchInput").value.trim();
            let resultsDiv = document.getElementById("results");
            resultsDiv.innerHTML = "";

            if (!query) {
                resultsDiv.innerHTML = "<p>الرجاء كتابة كلمة أو جزء من آية.</p>";
                return;
            }

            let results = ayat.filter(ayah => ayah.text.includes(query));
            if (results.length > 0) {
                results.forEach(result => {
                    resultsDiv.innerHTML += `<p><strong>${result.text}</strong><br>سورة ${result.surah} - آية ${result.number}</p><hr>`;
                });
            } else {
                resultsDiv.innerHTML = "<p>لم يتم العثور على نتائج.</p>";
            }
        }
    </script>
</body>
</html>
