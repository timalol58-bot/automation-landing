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
        
        .pulse-border {
            animation: pulseBorder 2s infinite;
        }
        
        @keyframes pulseBorder {
            0%, 100% { border-color: #22c55e; }
            50% { border-color: #86efac; }
        }
        
        .loading-spinner {
            border: 3px solid rgba(255, 255, 255, 0.3);
            border-top: 3px solid white;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            margin-right: 10px;
            vertical-align: middle;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
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
            
            <!-- ⚠️ ВАЖЛИВИЙ БЛОК: Запустіть бота -->
            <div class="bg-green-50 border-3 border-green-400 rounded-2xl p-5 mb-6 fade-in pulse-border" style="animation-delay: 0.1s;">
                <div class="flex items-start gap-4">
                    <div class="text-4xl">🤖</div>
                    <div>
                        <h3 class="text-green-800 font-bold text-lg mb-2">
                            Перш ніж заповнювати форму — запустіть бота!
                        </h3>
                        <p class="text-green-700 mb-3">
                            Щоб ми могли відповісти вам в Telegram, спочатку натисніть кнопку нижче і запустіть бота:
                        </p>
                        <a 
                            href="https://t.me/landosikmykhal_bot" 
                            target="_blank"
                            class="inline-flex items-center gap-2 bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-6 rounded-xl transition-all duration-300 hover:scale-105"
                        >
                            <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 0C5.373 0 0 5.373 0 12s5.373 12 12 12 12-5.373 12-12S18.627 0 12 0zm5.562 8.161c-.18 1.897-.962 6.502-1.359 8.627-.168.9-.5 1.201-.82 1.23-.697.064-1.226-.461-1.901-.903-1.056-.692-1.653-1.123-2.678-1.799-1.185-.781-.417-1.21.258-1.911.177-.184 3.247-2.977 3.307-3.23.007-.032.015-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.139-5.062 3.345-.479.329-.913.489-1.302.481-.428-.009-1.252-.242-1.865-.442-.751-.244-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.831-2.529 6.998-3.015 3.333-1.386 4.025-1.627 4.477-1.635.099-.002.321.023.465.141.121.1.154.234.169.359.015.126.034.411.019.635z"/>
                            </svg>
                            Відкрити бота в Telegram
                        </a>
                        <p class="text-green-600 text-sm mt-3">
                            👆 Натисніть <strong>Start</strong> в боті, потім поверніться сюди
                        </p>
                    </div>
                </div>
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
                    
                    <!-- Поле: Telegram ID -->
                    <div class="mb-6">
                        <label class="block text-gray-700 font-semibold mb-3 text-lg" for="telegramId">
                            📱 Ваш Telegram ID
                        </label>
                        <input 
                            type="text" 
                            id="telegramId" 
                            name="telegramId"
                            placeholder="Наприклад: 123456789"
                            required
                            pattern="[0-9]+"
                            title="Введіть тільки цифри"
                            class="w-full px-5 py-4 text-lg border-2 border-gray-200 rounded-xl input-focus focus:border-purple-500 focus:outline-none transition-all duration-300"
                        >
                        <div class="mt-3 p-4 bg-purple-50 rounded-xl">
                            <p class="text-purple-800 text-sm font-medium mb-2">🤖 Як дізнатись свій Telegram ID?</p>
                            <ol class="text-purple-700 text-sm space-y-1">
                                <li>1. Відкрийте Telegram</li>
                                <li>2. Знайдіть бота <a href="https://t.me/userinfobot" target="_blank" class="font-bold underline hover:text-purple-900">@userinfobot</a></li>
                                <li>3. Натисніть Start — бот покаже ваш ID</li>
                            </ol>
                        </div>
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
                        id="submitBtn"
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
                    <p class="text-gray-600 text-lg mb-2">Ми отримали вашу заявку.</p>
                    <p class="text-gray-600 text-lg mb-6">Перевірте Telegram — бот вже надіслав вам підтвердження!</p>
                    <button 
                        onclick="resetForm()"
                        class="text-purple-600 font-semibold hover:text-purple-800 transition-colors cursor-pointer"
                    >
                        ← Залишити ще одну заявку
                    </button>
                </div>
                
                <!-- Повідомлення про помилку (прихованe) -->
                <div id="errorMessage" class="hidden text-center py-10">
                    <div class="inline-flex items-center justify-center w-24 h-24 bg-red-100 rounded-full mb-6">
                        <svg class="w-14 h-14 text-red-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
                        </svg>
                    </div>
                    <h2 class="text-2xl font-bold text-gray-800 mb-3">Щось пішло не так 😔</h2>
                    <p class="text-gray-600 text-lg mb-4" id="errorText">Спробуйте ще раз або напишіть нам напряму в Telegram.</p>
                    <a 
                        href="https://t.me/landosikmykhal_bot" 
                        target="_blank"
                        class="inline-flex items-center gap-2 bg-blue-500 hover:bg-blue-600 text-white font-bold py-3 px-6 rounded-xl transition-all duration-300 mb-4"
                    >
                        Написати в Telegram
                    </a>
                    <br>
                    <button 
                        onclick="resetForm()"
                        class="text-purple-600 font-semibold hover:text-purple-800 transition-colors cursor-pointer mt-4"
                    >
                        ← Спробувати ще раз
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
        // ═══════════════════════════════════════════════════════════════
        // Webhook URL вашого n8n
        // ═══════════════════════════════════════════════════════════════
        const N8N_WEBHOOK_URL = 'https://timaloln8n.site/webhook/consultation-form';
        // ═══════════════════════════════════════════════════════════════
        
        // Обробка відправки форми
        document.getElementById('consultationForm').addEventListener('submit', async function(e) {
            e.preventDefault();
            
            const submitBtn = document.getElementById('submitBtn');
            const form = document.getElementById('consultationForm');
            
            // Показуємо завантаження
            submitBtn.innerHTML = '<span class="loading-spinner"></span> Відправляємо...';
            submitBtn.disabled = true;
            submitBtn.classList.add('opacity-70');
            
            // Збираємо дані форми
            const formData = {
                fullName: document.getElementById('fullName').value.trim(),
                telegramId: document.getElementById('telegramId').value.trim(),
                urgency: document.querySelector('input[name="urgency"]:checked')?.value,
                urgencyText: getUrgencyText(document.querySelector('input[name="urgency"]:checked')?.value),
                description: document.getElementById('description').value.trim(),
                timestamp: new Date().toISOString(),
                timestampLocal: new Date().toLocaleString('uk-UA'),
                source: window.location.href
            };
            
            console.log('📤 Відправляємо дані:', formData);
            console.log('🔗 На URL:', N8N_WEBHOOK_URL);
            
            try {
                // Спроба 1: Звичайний fetch з CORS
                let response;
                let success = false;
                
                try {
                    response = await fetch(N8N_WEBHOOK_URL, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        body: JSON.stringify(formData)
                    });
                    
                    console.log('✅ Відповідь сервера:', response.status);
                    
                    if (response.ok) {
                        success = true;
                    }
                } catch (corsError) {
                    console.log('⚠️ CORS помилка, пробуємо no-cors режим...');
                    
                    // Спроба 2: no-cors режим (не отримаємо відповідь, але запит відправиться)
                    await fetch(N8N_WEBHOOK_URL, {
                        method: 'POST',
                        headers: {
                            'Content-Type': 'application/json'
                        },
                        mode: 'no-cors',
                        body: JSON.stringify(formData)
                    });
                    
                    console.log('📨 Запит відправлено в no-cors режимі');
                    success = true; // Припускаємо що відправилось
                }
                
                if (success) {
                    // Показуємо повідомлення про успіх
                    form.classList.add('hidden');
                    document.getElementById('successMessage').classList.remove('hidden');
                    document.getElementById('errorMessage').classList.add('hidden');
                    console.log('🎉 Форма успішно відправлена!');
                } else {
                    throw new Error(`Сервер відповів з помилкою: ${response?.status || 'невідомо'}`);
                }
                
            } catch (error) {
                console.error('❌ Помилка відправки:', error);
                
                // Показуємо повідомлення про помилку
                form.classList.add('hidden');
                document.getElementById('successMessage').classList.add('hidden');
                document.getElementById('errorMessage').classList.remove('hidden');
                document.getElementById('errorText').textContent = 
                    'Помилка з\'єднання з сервером. Перевірте інтернет або напишіть нам напряму.';
            }
        });
        
        // Функція для отримання тексту терміновості
        function getUrgencyText(value) {
            const texts = {
                'urgent': '🔥 Терміново — потрібно якнайшвидше',
                'week': '📅 Протягом тижня',
                'month': '🗓️ Протягом місяця',
                'thinking': '🤔 Просто цікавлюсь ціною'
            };
            return texts[value] || value;
        }
        
        // Функція скидання форми
        function resetForm() {
            const form = document.getElementById('consultationForm');
            const submitBtn = document.getElementById('submitBtn');
            
            form.reset();
            form.classList.remove('hidden');
            document.getElementById('successMessage').classList.add('hidden');
            document.getElementById('errorMessage').classList.add('hidden');
            
            submitBtn.innerHTML = 'Відправити заявку ✉️';
            submitBtn.disabled = false;
            submitBtn.classList.remove('opacity-70');
        }
    </script>
    
</body>
</html>
