[index (1).html](https://github.com/user-attachments/files/24437827/index.1.html)
<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Автоматизація n8n — Залишити заявку</title>
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            font-family: 'Montserrat', sans-serif;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
        
        .card-shadow {
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }
        
        .input-focus:focus {
            box-shadow: 0 0 0 4px rgba(102, 126, 234, 0.3);
        }
        
        .btn-hover:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 40px rgba(102, 126, 234, 0.4);
        }
        
        .fade-in {
            animation: fadeIn 0.6s ease-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .radio-card:has(input:checked) {
            border-color: #667eea;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
        }
        
        .radio-card:has(input:checked) .radio-dot {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }
    </style>
</head>
<body class="min-h-screen gradient-bg">
    
    <!-- Головний контейнер -->
    <div class="min-h-screen py-8 px-4 flex items-center justify-center">
        <div class="w-full max-w-2xl">
            
            <!-- Логотип та заголовок -->
            <div class="text-center mb-8 fade-in">
                <div class="inline-flex items-center justify-center w-20 h-20 bg-white rounded-2xl card-shadow mb-6">
                    <svg class="w-12 h-12 text-purple-600" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
                    </svg>
                </div>
                <h1 class="text-3xl md:text-4xl font-bold text-white mb-3">
                    Автоматизація n8n
                </h1>
                <p class="text-white/80 text-lg">
                    Заповніть форму — ми зв'яжемося з вами!
                </p>
            </div>
            
            <!-- Картка з формою -->
            <div class="bg-white rounded-3xl card-shadow p-6 md:p-10 fade-in" style="animation-delay: 0.2s;">
                
                <form id="consultationForm">
                    
                    <!-- Поле: Прізвище та Ім'я -->
                    <div class="mb-6">
                        <label class="block text-gray-700 font-semibold mb-3 text-lg" for="fullName">
                            👤 Ваше прізвище та ім'я
                        </label>
                        <input 
                            type="text" 
                            id="fullName" 
                            name="fullName"
                            placeholder="Наприклад: Шевченко Тарас"
                            required
                            class="w-full px-5 py-4 text-lg border-2 border-gray-200 rounded-xl input-focus focus:border-purple-500 focus:outline-none transition-all duration-300"
                        >
                    </div>
                    
                    <!-- Поле: Telegram -->
                    <div class="mb-6">
                        <label class="block text-gray-700 font-semibold mb-3 text-lg" for="telegram">
                            📱 Ваш Telegram
                        </label>
                        <div class="relative">
                            <span class="absolute left-5 top-1/2 -translate-y-1/2 text-gray-400 text-lg">@</span>
                            <input 
                                type="text" 
                                id="telegram" 
                                name="telegram"
                                placeholder="ваш_нікнейм"
                                required
                                class="w-full pl-12 pr-5 py-4 text-lg border-2 border-gray-200 rounded-xl input-focus focus:border-purple-500 focus:outline-none transition-all duration-300"
                            >
                        </div>
                        <p class="text-gray-500 text-sm mt-2">Введіть ваш нікнейм без символу @</p>
                    </div>
                    
                    <!-- Поле: Терміновість -->
                    <div class="mb-6">
                        <label class="block text-gray-700 font-semibold mb-3 text-lg">
                            ⏰ Наскільки терміново вам потрібна автоматизація?
                        </label>
                        <div class="grid gap-3">
                            
                            <label class="radio-card flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer transition-all duration-300 hover:border-purple-300">
                                <input type="radio" name="urgency" value="urgent" required class="sr-only">
                                <div class="radio-dot w-5 h-5 rounded-full border-2 border-gray-300 mr-4 flex-shrink-0"></div>
                                <div>
                                    <span class="font-semibold text-gray-800">🔥 Терміново</span>
                                    <span class="text-gray-500 ml-2">— потрібно якнайшвидше</span>
                                </div>
                            </label>
                            
                            <label class="radio-card flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer transition-all duration-300 hover:border-purple-300">
                                <input type="radio" name="urgency" value="week" class="sr-only">
                                <div class="radio-dot w-5 h-5 rounded-full border-2 border-gray-300 mr-4 flex-shrink-0"></div>
                                <div>
                                    <span class="font-semibold text-gray-800">📅 Протягом тижня</span>
                                    <span class="text-gray-500 ml-2">— є трохи часу</span>
                                </div>
                            </label>
                            
                            <label class="radio-card flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer transition-all duration-300 hover:border-purple-300">
                                <input type="radio" name="urgency" value="month" class="sr-only">
                                <div class="radio-dot w-5 h-5 rounded-full border-2 border-gray-300 mr-4 flex-shrink-0"></div>
                                <div>
                                    <span class="font-semibold text-gray-800">🗓️ Протягом місяця</span>
                                    <span class="text-gray-500 ml-2">— не поспішаю</span>
                                </div>
                            </label>
                            
                            <label class="radio-card flex items-center p-4 border-2 border-gray-200 rounded-xl cursor-pointer transition-all duration-300 hover:border-purple-300">
                                <input type="radio" name="urgency" value="thinking" class="sr-only">
                                <div class="radio-dot w-5 h-5 rounded-full border-2 border-gray-300 mr-4 flex-shrink-0"></div>
                                <div>
                                    <span class="font-semibold text-gray-800">🤔 Просто цікавлюсь</span>
                                    <span class="text-gray-500 ml-2">— хочу дізнатись ціну</span>
                                </div>
                            </label>
                            
                        </div>
                    </div>
                    
                    <!-- Поле: Опис автоматизації -->
                    <div class="mb-8">
                        <label class="block text-gray-700 font-semibold mb-3 text-lg" for="description">
                            ✏️ Опишіть, що хочете автоматизувати
                        </label>
                        <textarea 
                            id="description" 
                            name="description"
                            rows="5"
                            placeholder="Розкажіть своїми словами, яку задачу ви хочете автоматизувати. Наприклад: 'Хочу, щоб коли клієнт заповнює форму на сайті, мені приходило повідомлення в Telegram і дані зберігались в Google таблицю'"
                            required
                            class="w-full px-5 py-4 text-lg border-2 border-gray-200 rounded-xl input-focus focus:border-purple-500 focus:outline-none transition-all duration-300 resize-none"
                        ></textarea>
                    </div>
                    
                    <!-- Кнопка відправки -->
                    <button 
                        type="submit"
                        class="w-full gradient-bg text-white font-bold text-xl py-5 rounded-xl btn-hover transition-all duration-300 cursor-pointer"
                    >
                        Відправити заявку ✉️
                    </button>
                    
                </form>
                
                <!-- Повідомлення про успіх (прихованe) -->
                <div id="successMessage" class="hidden text-center py-10">
                    <div class="inline-flex items-center justify-center w-24 h-24 bg-green-100 rounded-full mb-6">
                        <svg class="w-14 h-14 text-green-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/>
                        </svg>
                    </div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-3">Дякуємо за заявку! 🎉</h2>
                    <p class="text-gray-600 text-lg mb-6">Ми зв'яжемося з вами в Telegram найближчим часом.</p>
                    <button 
                        onclick="resetForm()"
                        class="text-purple-600 font-semibold hover:text-purple-800 transition-colors"
                    >
                        ← Залишити ще одну заявку
                    </button>
                </div>
                
            </div>
            
            <!-- Футер -->
            <div class="text-center mt-8 text-white/60">
                <p>© 2024 Автоматизація n8n. Всі права захищені.</p>
            </div>
            
        </div>
    </div>
    
    <script>
        // Обробка відправки форми
        document.getElementById('consultationForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Збираємо дані форми
            const formData = {
                fullName: document.getElementById('fullName').value,
                telegram: '@' + document.getElementById('telegram').value,
                urgency: document.querySelector('input[name="urgency"]:checked')?.value,
                description: document.getElementById('description').value
            };
            
            // Виводимо в консоль (для тестування)
            console.log('Нова заявка:', formData);
            
            // Показуємо повідомлення про успіх
            document.getElementById('consultationForm').classList.add('hidden');
            document.getElementById('successMessage').classList.remove('hidden');
        });
        
        // Функція скидання форми
        function resetForm() {
            document.getElementById('consultationForm').reset();
            document.getElementById('consultationForm').classList.remove('hidden');
            document.getElementById('successMessage').classList.add('hidden');
        }
    </script>
    
</body>
</html>
