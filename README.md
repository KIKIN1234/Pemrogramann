<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aplikasi Prediksi Penyakit Jantung</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Inter Font -->
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Style for custom radio buttons */
        .custom-radio input[type="radio"] {
            display: none;
        }
        .custom-radio label {
            padding: 0.5rem 1rem;
            border-radius: 9999px; /* rounded-full */
            cursor: pointer;
            transition: all 0.2s ease-in-out;
            font-weight: 600;
        }
        .custom-radio input[type="radio"]:checked + label {
            background-color: #3b82f6; /* blue-500 */
            color: white;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
        }
    </style>
</head>
<body class="bg-gray-100 min-h-screen p-4 flex items-center justify-center">

    <div class="max-w-4xl w-full bg-white rounded-xl shadow-2xl p-8 md:p-12">
        <!-- Header -->
        <div class="text-center mb-10">
            <h1 class="text-3xl md:text-4xl font-bold text-gray-800">Aplikasi Prediksi Penyakit Jantung</h1>
            <p class="mt-2 text-gray-600">Aplikasi ini memprediksi kemungkinan penyakit jantung berdasarkan fitur yang dimasukkan.</p>
        </div>

        <!-- Input Form -->
        <div id="form-section">
            <h2 class="text-2xl font-semibold text-gray-700 mb-6 border-b pb-2">Masukkan Data Pasien:</h2>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Column 1 -->
                <div class="flex flex-col gap-6">
                    <!-- Usia -->
                    <div class="space-y-2">
                        <label for="age" class="block font-medium text-gray-700">Usia: <span id="age-value" class="font-bold text-blue-600">50</span></label>
                        <input type="range" id="age" name="age" min="20" max="80" value="50" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <p class="text-sm text-gray-500">Usia pasien dalam tahun.</p>
                    </div>

                    <!-- Jenis Kelamin -->
                    <div class="space-y-2">
                        <span class="block font-medium text-gray-700">Jenis Kelamin</span>
                        <div class="flex space-x-4 custom-radio">
                            <input type="radio" id="sex-0" name="sex" value="0" checked>
                            <label for="sex-0" class="bg-gray-200 text-gray-700">Wanita</label>
                            <input type="radio" id="sex-1" name="sex" value="1">
                            <label for="sex-1" class="bg-gray-200 text-gray-700">Pria</label>
                        </div>
                    </div>

                    <!-- Tipe Nyeri Dada (cp) -->
                    <div class="space-y-2">
                        <label for="cp" class="block font-medium text-gray-700">Tipe Nyeri Dada (cp)</label>
                        <select id="cp" name="cp" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md shadow-sm">
                            <option value="0">0: Typical angina</option>
                            <option value="1">1: Atypical angina</option>
                            <option value="2">2: Non-anginal pain</option>
                            <option value="3">3: Asymptomatic</option>
                        </select>
                        <p class="text-sm text-gray-500">Jenis nyeri dada yang dialami pasien.</p>
                    </div>

                    <!-- Tekanan Darah Istirahat (trestbps) -->
                    <div class="space-y-2">
                        <label for="trestbps" class="block font-medium text-gray-700">Tekanan Darah Istirahat (trestbps): <span id="trestbps-value" class="font-bold text-blue-600">120</span></label>
                        <input type="range" id="trestbps" name="trestbps" min="90" max="200" value="120" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <p class="text-sm text-gray-500">Tekanan darah saat istirahat (mm Hg).</p>
                    </div>

                    <!-- Kolesterol Serum (chol) -->
                    <div class="space-y-2">
                        <label for="chol" class="block font-medium text-gray-700">Kolesterol Serum (chol): <span id="chol-value" class="font-bold text-blue-600">200</span></label>
                        <input type="range" id="chol" name="chol" min="100" max="600" value="200" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <p class="text-sm text-gray-500">Kolesterol serum (mg/dl).</p>
                    </div>

                    <!-- Gula Darah Puasa (fbs) -->
                    <div class="space-y-2">
                        <span class="block font-medium text-gray-700">Gula Darah Puasa > 120 mg/dl (fbs)</span>
                        <div class="flex space-x-4 custom-radio">
                            <input type="radio" id="fbs-0" name="fbs" value="0" checked>
                            <label for="fbs-0" class="bg-gray-200 text-gray-700">Tidak</label>
                            <input type="radio" id="fbs-1" name="fbs" value="1">
                            <label for="fbs-1" class="bg-gray-200 text-gray-700">Ya</label>
                        </div>
                    </div>
                </div>

                <!-- Column 2 -->
                <div class="flex flex-col gap-6">
                    <!-- EKG Istirahat (restecg) -->
                    <div class="space-y-2">
                        <label for="restecg" class="block font-medium text-gray-700">Hasil Elektrokardiografi Istirahat (restecg)</label>
                        <select id="restecg" name="restecg" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md shadow-sm">
                            <option value="0">0: Normal</option>
                            <option value="1">1: Kelainan gelombang ST-T</option>
                            <option value="2">2: Hipertrofi ventrikel kiri</option>
                        </select>
                        <p class="text-sm text-gray-500">Hasil elektrokardiografi saat istirahat.</p>
                    </div>
                    
                    <!-- Detak Jantung Maksimum (thalach) -->
                    <div class="space-y-2">
                        <label for="thalach" class="block font-medium text-gray-700">Detak Jantung Maksimum (thalach): <span id="thalach-value" class="font-bold text-blue-600">150</span></label>
                        <input type="range" id="thalach" name="thalach" min="70" max="202" value="150" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <p class="text-sm text-gray-500">Detak jantung maksimum yang tercapai.</p>
                    </div>

                    <!-- Angina Akibat Olahraga (exang) -->
                    <div class="space-y-2">
                        <span class="block font-medium text-gray-700">Angina Akibat Olahraga (exang)</span>
                        <div class="flex space-x-4 custom-radio">
                            <input type="radio" id="exang-0" name="exang" value="0" checked>
                            <label for="exang-0" class="bg-gray-200 text-gray-700">Tidak</label>
                            <input type="radio" id="exang-1" name="exang" value="1">
                            <label for="exang-1" class="bg-gray-200 text-gray-700">Ya</label>
                        </div>
                    </div>

                    <!-- Depresi ST Akibat Olahraga (oldpeak) -->
                    <div class="space-y-2">
                        <label for="oldpeak" class="block font-medium text-gray-700">Depresi ST Akibat Olahraga (oldpeak): <span id="oldpeak-value" class="font-bold text-blue-600">1.0</span></label>
                        <input type="range" id="oldpeak" name="oldpeak" min="0.0" max="6.0" value="1.0" step="0.1" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        <p class="text-sm text-gray-500">Depresi ST yang diinduksi olahraga relatif terhadap istirahat.</p>
                    </div>

                    <!-- Slope Puncak Segment ST Olahraga (slope) -->
                    <div class="space-y-2">
                        <label for="slope" class="block font-medium text-gray-700">Slope Puncak Segment ST Olahraga (slope)</label>
                        <select id="slope" name="slope" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md shadow-sm">
                            <option value="0">0: Upsloping</option>
                            <option value="1">1: Flat</option>
                            <option value="2">2: Downsloping</option>
                        </select>
                        <p class="text-sm text-gray-500">Slope dari segmen ST olahraga.</p>
                    </div>

                    <!-- Jumlah Pembuluh Darah Besar (ca) -->
                    <div class="space-y-2">
                        <label for="ca" class="block font-medium text-gray-700">Jumlah Pembuluh Darah Besar (ca)</label>
                        <select id="ca" name="ca" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md shadow-sm">
                            <option value="0">0</option>
                            <option value="1">1</option>
                            <option value="2">2</option>
                            <option value="3">3</option>
                        </select>
                        <p class="text-sm text-gray-500">Jumlah pembuluh darah besar (0-3) yang diwarnai oleh fluoroscopy.</p>
                    </div>
                </div>
            </div>

            <!-- Thal -->
            <div class="mt-6 space-y-2">
                <label for="thal" class="block font-medium text-gray-700">Thal (thal)</label>
                <select id="thal" name="thal" class="mt-1 block w-full pl-3 pr-10 py-2 text-base border-gray-300 focus:outline-none focus:ring-blue-500 focus:border-blue-500 sm:text-sm rounded-md shadow-sm">
                    <option value="0">0: Normal</option>
                    <option value="1">1: Fixed defect</option>
                    <option value="2">2: Reversible defect</option>
                    <option value="3">3: Tidak diketahui</option>
                </select>
                <p class="text-sm text-gray-500">Hasil tes stres thallium.</p>
            </div>
            
            <!-- Prediction Button -->
            <div class="flex justify-center mt-8">
                <button id="predict-button" class="w-full md:w-auto px-8 py-3 bg-blue-600 text-white font-bold rounded-lg shadow-lg hover:bg-blue-700 transition duration-300 ease-in-out transform hover:scale-105 focus:outline-none focus:ring-4 focus:ring-blue-500 focus:ring-opacity-50">
                    Prediksi
                </button>
            </div>
        </div>
        
        <!-- Prediction Result Section -->
        <div id="result-section" class="hidden mt-10">
            <hr class="border-gray-300 mb-6">
            <h2 class="text-2xl font-semibold text-gray-700 mb-4">Hasil Prediksi:</h2>
            <div id="result-content">
                <!-- Result will be injected here -->
            </div>
            <div class="mt-6 p-4 bg-yellow-100 border-l-4 border-yellow-500 text-yellow-700 rounded-md">
                <p class="font-semibold">Catatan:</p>
                <p class="text-sm">Prediksi ini hanyalah model statistik dan tidak menggantikan diagnosis medis profesional.</p>
            </div>
        </div>

        <!-- Loading Indicator -->
        <div id="loading-indicator" class="hidden text-center mt-10">
            <div class="animate-spin rounded-full h-12 w-12 border-4 border-blue-500 border-t-transparent mx-auto"></div>
            <p class="mt-4 text-blue-600 font-semibold">Memprediksi...</p>
        </div>

        <!-- Error Message -->
        <div id="error-message" class="hidden mt-10 p-4 bg-red-100 border-l-4 border-red-500 text-red-700 rounded-md">
            <p class="font-semibold">Error:</p>
            <p id="error-text" class="text-sm"></p>
        </div>

    </div>

    <script>
        // Get references to all input elements and display value spans
        const ageSlider = document.getElementById('age');
        const ageValueSpan = document.getElementById('age-value');
        const trestbpsSlider = document.getElementById('trestbps');
        const trestbpsValueSpan = document.getElementById('trestbps-value');
        const cholSlider = document.getElementById('chol');
        const cholValueSpan = document.getElementById('chol-value');
        const thalachSlider = document.getElementById('thalach');
        const thalachValueSpan = document.getElementById('thalach-value');
        const oldpeakSlider = document.getElementById('oldpeak');
        const oldpeakValueSpan = document.getElementById('oldpeak-value');
        const predictButton = document.getElementById('predict-button');
        const resultSection = document.getElementById('result-section');
        const resultContent = document.getElementById('result-content');
        const loadingIndicator = document.getElementById('loading-indicator');
        const errorMessage = document.getElementById('error-message');
        const errorText = document.getElementById('error-text');

        // Update slider value displays dynamically
        ageSlider.addEventListener('input', (e) => ageValueSpan.textContent = e.target.value);
        trestbpsSlider.addEventListener('input', (e) => trestbpsValueSpan.textContent = e.target.value);
        cholSlider.addEventListener('input', (e) => cholValueSpan.textContent = e.target.value);
        thalachSlider.addEventListener('input', (e) => thalachValueSpan.textContent = e.target.value);
        oldpeakSlider.addEventListener('input', (e) => oldpeakValueSpan.textContent = e.target.value);

        // Function to handle the API call and exponential backoff
        async function fetchWithBackoff(url, options, retries = 3, delay = 1000) {
            for (let i = 0; i < retries; i++) {
                try {
                    const response = await fetch(url, options);
                    if (response.status === 429) { // Too Many Requests
                        if (i < retries - 1) {
                            await new Promise(resolve => setTimeout(resolve, delay));
                            delay *= 2; // Exponential backoff
                            continue;
                        } else {
                            throw new Error("API request failed after multiple retries due to rate limiting.");
                        }
                    }
                    return response;
                } catch (error) {
                    if (i < retries - 1) {
                        await new Promise(resolve => setTimeout(resolve, delay));
                        delay *= 2; // Exponential backoff
                        continue;
                    }
                    throw error;
                }
            }
        }

        // Main prediction function
        predictButton.addEventListener('click', async () => {
            // Hide previous results and errors
            resultSection.classList.add('hidden');
            errorMessage.classList.add('hidden');
            resultContent.innerHTML = '';
            loadingIndicator.classList.remove('hidden');

            // Collect all input data
            const inputData = {
                age: parseInt(document.getElementById('age').value),
                sex: parseInt(document.querySelector('input[name="sex"]:checked').value),
                cp: parseInt(document.getElementById('cp').value),
                trestbps: parseInt(document.getElementById('trestbps').value),
                chol: parseInt(document.getElementById('chol').value),
                fbs: parseInt(document.querySelector('input[name="fbs"]:checked').value),
                restecg: parseInt(document.getElementById('restecg').value),
                thalach: parseInt(document.getElementById('thalach').value),
                exang: parseInt(document.querySelector('input[name="exang"]:checked').value),
                oldpeak: parseFloat(document.getElementById('oldpeak').value),
                slope: parseInt(document.getElementById('slope').value),
                ca: parseInt(document.getElementById('ca').value),
                thal: parseInt(document.getElementById('thal').value),
            };

            // Construct the prompt for the Gemini API
            const prompt = `
                Berperanlah sebagai model prediksi penyakit jantung. Saya akan memberikan data pasien, dan Anda akan memberikan prediksi apakah pasien memiliki penyakit jantung atau tidak, serta probabilitasnya.

                Fitur input:
                - age (Usia)
                - sex (Jenis Kelamin: 0=Wanita, 1=Pria)
                - cp (Tipe Nyeri Dada: 0-3)
                - trestbps (Tekanan Darah Istirahat)
                - chol (Kolesterol Serum)
                - fbs (Gula Darah Puasa > 120 mg/dl: 0=Tidak, 1=Ya)
                - restecg (Hasil EKG Istirahat: 0-2)
                - thalach (Detak Jantung Maksimum)
                - exang (Angina Akibat Olahraga: 0=Tidak, 1=Ya)
                - oldpeak (Depresi ST Akibat Olahraga)
                - slope (Slope Puncak Segment ST: 0-2)
                - ca (Jumlah Pembuluh Darah Besar: 0-3)
                - thal (Thal: 0-3)
                
                Data pasien yang diberikan:
                ${JSON.stringify(inputData)}
                
                Berikan respons Anda dalam format JSON berikut. Nilai 'prediction' adalah 1 jika pasien kemungkinan besar mengalami penyakit jantung, dan 0 jika tidak. Probabilitas harus dalam format [prob_tidak_sakit, prob_sakit]. Berikan prediksi yang masuk akal berdasarkan data input.
            `;

            const payload = {
                contents: [{
                    role: "user",
                    parts: [{ text: prompt }]
                }],
                generationConfig: {
                    responseMimeType: "application/json",
                    responseSchema: {
                        type: "OBJECT",
                        properties: {
                            "prediction": { "type": "NUMBER" },
                            "probabilities": {
                                "type": "ARRAY",
                                "items": { "type": "NUMBER" }
                            }
                        },
                        "propertyOrdering": ["prediction", "probabilities"]
                    }
                }
            };
            
            const apiKey = ""; // Canvas will provide this in runtime
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;

            try {
                const response = await fetchWithBackoff(apiUrl, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(payload)
                });

                if (!response.ok) {
                    throw new Error(`HTTP error! status: ${response.status}`);
                }

                const result = await response.json();
                const jsonText = result?.candidates?.[0]?.content?.parts?.[0]?.text;

                if (jsonText) {
                    const data = JSON.parse(jsonText);
                    const prediction = data.prediction;
                    const probabilities = data.probabilities;
                    
                    const probNoDisease = (probabilities[0] * 100).toFixed(2);
                    const probDisease = (probabilities[1] * 100).toFixed(2);
                    
                    let resultHtml = '';
                    if (prediction === 1) {
                        resultHtml = `
                            <div class="p-6 bg-red-100 border-l-4 border-red-500 text-red-700 rounded-lg shadow-md">
                                <p class="font-bold text-xl mb-2">Berdasarkan data yang dimasukkan, pasien memiliki kemungkinan besar <span class="font-extrabold">MENGALAMI Penyakit Jantung.</span></p>
                                <p class="text-lg">Probabilitas Penyakit Jantung: <span class="font-bold">${probDisease}%</span></p>
                                <p class="text-sm">Probabilitas Tidak Ada Penyakit Jantung: ${probNoDisease}%</p>
                            </div>
                        `;
                    } else {
                        resultHtml = `
                            <div class="p-6 bg-green-100 border-l-4 border-green-500 text-green-700 rounded-lg shadow-md">
                                <p class="font-bold text-xl mb-2">Berdasarkan data yang dimasukkan, pasien memiliki kemungkinan kecil <span class="font-extrabold">MENGALAMI Penyakit Jantung.</span></p>
                                <p class="text-lg">Probabilitas Tidak Ada Penyakit Jantung: <span class="font-bold">${probNoDisease}%</span></p>
                                <p class="text-sm">Probabilitas Penyakit Jantung: ${probDisease}%</p>
                            </div>
                        `;
                    }
                    resultContent.innerHTML = resultHtml;
                    resultSection.classList.remove('hidden');

                } else {
                    throw new Error("Respons API tidak valid.");
                }

            } catch (e) {
                console.error("Prediction error:", e);
                errorText.textContent = `Terjadi kesalahan saat melakukan prediksi: ${e.message}`;
                errorMessage.classList.remove('hidden');
            } finally {
                loadingIndicator.classList.add('hidden');
            }
        });
    </script>
</body>
</html>
