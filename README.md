```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Horario de Estudio</title>
    <style>
        /* Estilos básicos para que se vea algo similar, se pueden mejorar mucho más con Tailwind CSS */
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(to right, #f0fdf4, #e0f2fe); /* Similar a Tailwind bg-gradient-to-br from-teal-50 to-cyan-100 */
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
            color: #374151; /* Similar to Tailwind text-gray-700 */
        }
        .schedule-container {
            width: 100%;
            max-width: 800px; /* Adjust as needed */
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 32px; /* Similar to Tailwind gap-8 */
        }
        .schedule-card {
            background-color: #ffffff;
            padding: 24px; /* Similar to Tailwind p-6 */
            border-radius: 24px; /* Similar to Tailwind rounded-3xl */
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25); /* Similar to Tailwind shadow-xl */
            border: 4px solid #93c5fd; /* Similar to Tailwind border-indigo-300 */
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
            transform: scale(1); /* Default scale */
            transition: transform 0.3s ease-in-out; /* Similar to Tailwind transition-transform duration-300 ease-in-out */
            font-family: 'Inter', sans-serif;
        }
        .schedule-card:hover {
            transform: scale(1.02); /* Similar to Tailwind hover:scale-105, adjusted slightly for better effect */
        }
        .title-section {
            text-align: center;
            margin-bottom: 24px; /* Similar to Tailwind mb-6 */
            width: 100%;
        }
        .title-section h2 {
            font-size: 2.5rem; /* Similar to Tailwind text-4xl */
            font-weight: 800; /* Similar to Tailwind font-extrabold */
            color: #1e3a8a; /* Similar to Tailwind text-blue-800 */
            margin-bottom: 8px; /* Similar to Tailwind mb-2 */
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.05); /* Similar to Tailwind drop-shadow-md */
        }
        .title-section h3 {
            font-size: 1.5rem; /* Similar to Tailwind text-2xl */
            font-weight: 700; /* Similar to Tailwind font-bold */
            text-transform: uppercase; /* Similar to Tailwind uppercase */
            letter-spacing: 0.05em; /* Similar to Tailwind tracking-wider */
            color: #047857; /* Similar to Tailwind text-emerald-700 */
        }
        .title-section span.date {
            font-size: 1.875rem; /* Similar to Tailwind text-3xl */
            color: #3b82f6; /* Similar to Tailwind text-indigo-600 */
        }
        .title-section p {
            font-size: 1.125rem; /* Similar to Tailwind text-lg */
            color: #4b5563; /* Similar to Tailwind text-gray-700 */
            margin-top: 8px; /* Similar to Tailwind mt-2 */
            font-weight: 600; /* Similar to Tailwind font-semibold */
        }
        .title-section span.study-hours {
            color: #166534; /* Similar to Tailwind text-green-700 */
            font-weight: 800; /* Similar to Tailwind font-extrabold */
        }
        .activities-list {
            display: flex;
            flex-direction: column;
            width: 100%;
            gap: 16px; /* Similar to Tailwind space-y-4 */
        }
        .activity-item {
            display: flex;
            align-items: flex-start;
            padding: 16px; /* Similar to Tailwind p-4 */
            border-radius: 8px; /* Similar to Tailwind rounded-xl */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1); /* Similar to Tailwind shadow-md */
            transition: background-color 0.2s ease-in-out, border-color 0.2s ease-in-out; /* Similar to Tailwind transition-all duration-200 ease-in-out */
            border-left-width: 8px; /* Similar to Tailwind border-l-8 */
        }
        .activity-item-study { background-color: #f0fdf4; border-left-color: #84cc17; } /* Similar to bg-lime-50 border-l-8 border-lime-400 */
        .activity-item-study:hover { background-color: #d9f7da; } /* Similar to hover:bg-lime-100 */
        .activity-item-meal { background-color: #fff7ed; border-left-color: #f59e0b; } /* Similar to bg-amber-50 border-l-8 border-amber-400 */
        .activity-item-meal:hover { background-color: #fffaeb; } /* Similar to hover:bg-amber-100 */
        .activity-item-snack { background-color: #fff7eb; border-left-color: #f97316; } /* Similar to bg-orange-50 border-l-8 border-orange-400 */
        .activity-item-snack:hover { background-color: #fff6e0; } /* Similar to hover:bg-orange-100 */
        .activity-item-leisure { background-color: #f3e8ff; border-left-color: #a855f7; } /* Similar to bg-violet-50 border-l-8 border-violet-400 */
        .activity-item-leisure:hover { background-color: #fbf8ff; } /* Similar to hover:bg-violet-100 */
        .activity-item-productivity { background-color: #fee2e2; border-left-color: #ef4444; } /* Similar to bg-rose-50 border-l-8 border-rose-400 */
        .activity-item-productivity:hover { background-color: #fdecea; } /* Similar to hover:bg-rose-100 */
        .activity-item-personal { background-color: #f0f9ff; border-left-color: #0ea5e9; } /* Similar to bg-sky-50 border-l-8 border-sky-400 */
        .activity-item-personal:hover { background-color: #f0f9ff; } /* Similar to hover:bg-sky-100 */
        .activity-item-sleep { background-color: #f8fafc; border-left-color: #6b7280; } /* Similar to bg-blue-gray-50 border-l-8 border-blue-gray-400 */
        .activity-item-sleep:hover { background-color: #f0f2f5; } /* Similar to hover:bg-blue-gray-100 */
        .activity-item-study-red { background-color: #fee2e2; border-left-color: #dc2626; } /* Similar to bg-red-50 border-l-8 border-red-400 */
        .activity-item-study-red:hover { background-color: #fdecea; } /* Similar to hover:bg-red-100 */

        .activity-icon {
            flex-shrink: 0;
            margin-right: 12px; /* Similar to Tailwind mr-3 */
            margin-top: 1px; /* Similar to Tailwind mt-0.5 */
            font-size: 1.5rem; /* Similar to Tailwind text-2xl */
            display: flex; /* Ensure icons are treated as block elements for consistent alignment */
            align-items: center;
        }
        .activity-content {
            flex-grow: 1;
        }
        .activity-time {
            font-size: 1.25rem; /* Similar to Tailwind text-xl */
            font-weight: 800; /* Similar to Tailwind font-extrabold */
            color: #1f2937; /* Similar to Tailwind text-gray-900 */
            line-height: 1.2; /* Similar to Tailwind leading-tight */
            margin-bottom: 4px; /* Similar to Tailwind mb-1 */
        }
        .activity-description {
            font-size: 1.125rem; /* Similar to Tailwind text-lg */
            color: #4b5563; /* Similar to Tailwind text-gray-700 */
            font-weight: 500; /* Similar to Tailwind font-medium */
        }

        /* Placeholder for Lucide Icons (you'd typically use an SVG library or CDN) */
        /* For demonstration purposes, we'll use simple text placeholders */
        .icon-placeholder {
            display: inline-block;
            width: 24px;
            height: 24px;
            text-align: center;
            line-height: 24px;
            border-radius: 4px;
            font-size: 1.2rem; /* Adjust size as needed */
        }
        .icon-bath { color: #0ea5e9; } /* text-sky-500 */
        .icon-utensils { color: #d97706; } /* text-amber-600 */
        .icon-apple { color: #f59e0b; } /* text-orange-500 */
        .icon-gamepad { color: #a855f7; } /* text-violet-600 */
        .icon-sun { color: #f59e0b; } /* text-amber-600 */
        .icon-moon { color: #64748b; } /* text-gray-500 or text-blue-gray-600 */
        .icon-zap { color: #e11d48; } /* text-red-600 */
        .icon-list-todo { color: #e11d48; } /* text-rose-500 */
        .icon-film { color: #e11d48; } /* text-rose-500 */
        .icon-brain { color: #e11d48; } /* text-rose-500 */
        .icon-lightbulb { color: #e11d48; } /* text-rose-500 */

        /* For the 'Study' icon that's red */
        .icon-book-red { color: #dc2626; } /* text-red-600 */

    </style>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
</head>
<body>
    <div class="schedule-container">
        <!-- Schedule Card 1 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Física – energía</h2>
                <h3 class="text-center">Sábado, <span class="date">28 jun</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Pan con queso y aguacate)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Termodinámica</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Arroz con huevo y plátano)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Manzana y un puñado de frutos secos)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Energía y trabajo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Leyes de Newton</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox retos mentales</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Flashcards y apuntes de conceptos clave</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin rápidos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 2 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Lectura Crítica: Inferencia y actitudinal</h2>
                <h3 class="text-center">Domingo, <span class="date">29 jun</span></h3>
                <p>Horas de estudio: <span class="study-hours">6.5h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Tostadas con mermelada y queso fresco)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Inferencias (8 textos)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Sopa y pan integral)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Batido de frutas con espinacas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 5:00 PM</p>
                        <p class="activity-description">Estudio 📚: Práctica cronometrada y Actitudinales (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:00 PM - 7:00 PM</p>
                        <p class="activity-description">Estudio 📚: Actitudinales (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:00 PM - 7:45 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai ritmo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:45 PM</p>
                        <p class="activity-description">Productividad 📝: Resumir errores y ver videos explicativos sobre interpretación textual 🎬</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:45 PM - 9:30 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Roblox creativo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 3 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Álgebra y funciones</h2>
                <h3 class="text-center">Lunes, <span class="date">30 jun</span></h3>
                <p>Horas de estudio: <span class="study-hours">6.5h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Arepa con huevo y fruta)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ecuaciones I y II grado</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pasta con queso y ensalada)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍬</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍬 (Galletas de arroz con crema de cacahuete)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Funciones lineales/cuadráticas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 7:00 PM</p>
                        <p class="activity-description">Estudio 📚: Problemas tipo ICFES (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:00 PM - 7:45 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin eventos diarios</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-brain">🧠</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:45 PM</p>
                        <p class="activity-description">Productividad 🧠: Mapas mentales de fórmulas y resolución de ejercicios desafiantes 💡</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:45 PM - 9:30 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 4 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Historia de Colombia</h2>
                <h3 class="text-center">Martes, <span class="date">1 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">7h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Fruta con yogurt y avena)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Precolombina</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Emparedado de pollo con vegetales)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Rodajas de pepino con hummus)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 5:00 PM</p>
                        <p class="activity-description">Estudio 📚: Independencia y república (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:00 PM - 7:30 PM</p>
                        <p class="activity-description">Estudio 📚: Preguntas oficiales (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍪</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:30 PM - 7:45 PM</p>
                        <p class="activity-description">Refrigerio 🍪 (Un huevo cocido y una mandarina)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:30 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox en equipo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:30 PM - 9:30 PM</p>
                        <p class="activity-description">Productividad ✍️: Cronología en Word y ver documentales históricos 🎬</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 10:15 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:15 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 5 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Inglés: Comprensión lectora</h2>
                <h3 class="text-center">Miércoles, <span class="date">2 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Sándwich integral con vegetales)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Textos académicos + vocabulario</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pollo al horno con ensalada)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Pera y un trozo de queso)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Preguntas abiertas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Vocabulario específico</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Crear flashcards y practicar con apps de conversación en inglés 🗣️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 6 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Biología celular</h2>
                <h3 class="text-center">Jueves, <span class="date">3 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Ensalada ligera de frutas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Estructura y función</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Arroz y vegetales con proteína vegetal)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Smoothie de vegetales y proteína)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Metabolismo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ciclo celular</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin misiones</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Diagrama en papel de procesos biológicos y ver videos de microscopía 🔬</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 7 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Estructura textual</h2>
                <h3 class="text-center">Viernes, <span class="date">4 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Huevos revueltos con tostadas y tomate)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Tesis y argumentos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Sopa con pan y ensalada pequeña)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Plátano y un puñado de nueces)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Textos largos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Estructura de párrafos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox creativo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Resumen estructurado de textos y práctica de escritura de ensayos cortos ✍️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 8 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Estadística básica</h2>
                <h3 class="text-center">Sábado, <span class="date">5 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Arepa con queso y café)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Medias, medianas, modas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Lentejas con arroz y plátano maduro)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Rebanadas de manzana con mantequilla de almendras)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Gráficas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ejercicios tipo ICFES</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Crear gráficas en papel y análisis de datos de ejemplos reales 📈</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 9 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Simulacro por áreas</h2>
                <h3 class="text-center">Domingo, <span class="date">6 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Desayuno completo y nutritivo)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Simulacro Lectura (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pollo con vegetales al vapor)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Naranja en gajos y un puñado de maní)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Simulacro Matemáticas (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Simulacro Naturales (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Corrección de errores y repaso intensivo de temas débiles 🔍</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 10 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Geografía de Colombia</h2>
                <h3 class="text-center">Lunes, <span class="date">7 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">7h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Fruta con cereal integral)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Regiones naturales (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pollo con arroz y frijoles)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Galletas de arroz con aguacate)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 5:00 PM</p>
                        <p class="activity-description">Estudio 📚: Dinámica poblacional (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:00 PM - 7:30 PM</p>
                        <p class="activity-description">Estudio 📚: Mapas y coordenadas (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍪</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:30 PM - 7:45 PM</p>
                        <p class="activity-description">Refrigerio 🍪 (Un puñado de pistachos y unas fresas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:30 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox mapas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">🧠</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:30 PM - 9:30 PM</p>
                        <p class="activity-description">Productividad 🧠: Crear mapa mental interactivo y visualizar documentales geográficos 🗺️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 10:15 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:15 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 11 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Listening ICFES</h2>
                <h3 class="text-center">Martes, <span class="date">8 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Omelette con espinacas y queso)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Audios oficiales</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Estofado de carne con vegetales)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Yogurt griego con miel)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Discriminación auditiva</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Listening preguntas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin eventos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Repaso de audios y práctica de pronunciación con grabadora 🗣️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 12 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Ecología y ambiente</h2>
                <h3 class="text-center">Miércoles, <span class="date">9 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Granola con fruta fresca y leche)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ecosistemas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pasta con salsa de tomate y champiñones)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Vegetales cortados con dip de yogur)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Impacto ambiental</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Sostenibilidad</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Apuntes visuales y lectura de informes ambientales 🌳</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 13 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Argumentación</h2>
                <h3 class="text-center">Jueves, <span class="date">10 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Huevos rancheros)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Falacias</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Sopa de lentejas con crutones)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Galletas de arroz con queso crema y jamón)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Práctica argumentación</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ejercicios oficiales</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox creativo</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">🗣️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 🗣️: Debate simulado con un tema ICFES y lectura de columnas de opinión 📰</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 14 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Probabilidad básica</h2>
                <h3 class="text-center">Viernes, <span class="date">11 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Batido de proteínas y tostadas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Eventos y muestras</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Carne magra con arroz integral y brócoli)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Rodajas de pera y un puñado de pasas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ejercicios tipo examen</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Problemas probabilidad</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Crear tablas de resultados y resolver problemas de lógica y razonamiento cuantitativo 🔢</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 15 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Constitución y derechos</h2>
                <h3 class="text-center">Sábado, <span class="date">12 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">7h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Fruta fresca con queso cottage)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Artículos clave (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Arroz con pollo y aguacate)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Batido de yogur y bayas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 5:00 PM</p>
                        <p class="activity-description">Estudio 📚: Casos prácticos (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:00 PM - 7:30 PM</p>
                        <p class="activity-description">Estudio 📚: Derechos fundamentales (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍬</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:30 PM - 7:45 PM</p>
                        <p class="activity-description">Refrigerio 🍬 (Mini sándwich de atún)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:30 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:30 PM - 9:30 PM</p>
                        <p class="activity-description">Productividad ✍️: Crear esquema de artículos y analizar noticias relacionadas con derechos civiles ⚖️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 10:15 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:15 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 16 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Simulacro mixto</h2>
                <h3 class="text-center">Domingo, <span class="date">13 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Desayuno completo para energía)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: 2 secciones simulacro</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pollo a la plancha con vegetales asados)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Puñado de almendras y arándanos)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: 2 secciones simulacro</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Revisión y corrección</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Análisis de errores y planificación detallada de la próxima semana de estudio 📅</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 17 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Física – energía</h2>
                <h3 class="text-center">Lunes, <span class="date">14 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Jugo de naranja natural y tostada integral con huevo)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Termodinámica avanzada</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Arroz con pollo desmechado y ensalada)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Un puñado de uvas y un trozo de queso)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Energía y trabajo avanzado</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Newton aplicaciones</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Simulación de problemas de física complejos y ver videos de experimentos científicos 🧪</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 18 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Reading ICFES</h2>
                <h3 class="text-center">Martes, <span class="date">15 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Ensalada de frutas con yogur)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Lecturas largas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pechuga de pollo a la plancha con puré de papa)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Tostadas integrales con aguacate)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Preguntas abiertas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Vocabulario en contexto</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Crear flashcards y leer artículos de noticias en inglés para mejorar vocabulario 🗞️</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 19 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Geometría y áreas</h2>
                <h3 class="text-center">Miércoles, <span class="date">16 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Fruta con granola y miel)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Áreas y perímetros</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pasta con vegetales y carne molida)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Yogurt con un poco de cereal)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Problemas ICFES</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Teoremas geometría</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Ejercicios de visualización espacial y revisión de fórmulas geométricas con demostraciones 📐</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 20 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Economía colombiana</h2>
                <h3 class="text-center">Jueves, <span class="date">17 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">7h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Arepa con queso y café con leche)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: PIB y sectores (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Guiso de carne con papa y arroz)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Batido de frutas con espinacas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 5:00 PM</p>
                        <p class="activity-description">Estudio 📚: Indicadores sociales (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:00 PM - 7:30 PM</p>
                        <p class="activity-description">Estudio 📚: Crecimiento y desarrollo (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍪</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:30 PM - 7:45 PM</p>
                        <p class="activity-description">Refrigerio 🍪 (Puñado de maní y pasas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:45 PM - 8:30 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox simulación</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:30 PM - 9:30 PM</p>
                        <p class="activity-description">Productividad ✍️: Crear tablas de indicadores y analizar casos de estudio económico de Colombia 📊</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:30 PM - 10:15 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:15 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 21 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Química orgánica</h2>
                <h3 class="text-center">Viernes, <span class="date">18 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Ensalada de frutas con yogur y granola)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Hidrocarburos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Lentejas guisadas con arroz)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Zanahorias baby y pepino en rodajas)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Reacciones orgánicas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Ejercicios ICFES</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad 📝: Dibujar estructuras químicas y ver videos sobre reacciones orgánicas en 3D 🧪</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 22 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Síntesis</h2>
                <h3 class="text-center">Sábado, <span class="date">19 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Tostadas con mermelada y un vaso de leche)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Redacción de síntesis</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Pechuga de pollo al vapor con vegetales)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Yogur bebible y un banano)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:30 PM</p>
                        <p class="activity-description">Estudio 📚: Textos mixtos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:30 PM - 6:30 PM</p>
                        <p class="activity-description">Estudio 📚: Reformulación de ideas</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">6:30 PM - 7:15 PM</p>
                        <p class="activity-description">Juegos 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">✍️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:15 PM</p>
                        <p class="activity-description">Productividad ✍️: Practicar síntesis en Word y escuchar podcasts sobre técnicas de redacción 🎧</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🌌</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 12:30 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🌌: Genshin</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 23 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Simulacro final y retroalimentación</h2>
                <h3 class="text-center">Domingo, <span class="date">20 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">7h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Desayuno completo y energético)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 2:00 PM</p>
                        <p class="activity-description">Estudio 📚: Simulacro 2 secciones (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:00 PM - 2:45 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Arroz con huevo y salchichas de pollo)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:45 PM - 3:00 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Rodajas de piña y un puñado de pistachos)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">3:00 PM - 5:30 PM</p>
                        <p class="activity-description">Estudio 📚: Simulacro 3 secciones (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study-red">
                    <span class="activity-icon"><span class="icon-placeholder icon-zap">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">5:30 PM - 7:30 PM</p>
                        <p class="activity-description">Estudio 📚: Revisión detallada (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-gamepad">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:30 PM - 8:15 PM</p>
                        <p class="activity-description">Juegos 🎮: Roblox retos</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-list-todo">📝</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:15 PM - 9:15 PM</p>
                        <p class="activity-description">Productividad 📝: Análisis exhaustivo de errores y preparación mental para el examen 🧘</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:15 PM - 10:00 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎶</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎶: Project Sekai</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Schedule Card 24 -->
        <div class="schedule-card">
            <div class="title-section">
                <h2 class="text-center">Tema: Repaso suave y reflexión</h2>
                <h3 class="text-center">Lunes, <span class="date">21 jul</span></h3>
                <p>Horas de estudio: <span class="study-hours">6.75h</span></p>
            </div>
            <div class="activities-list">
                <div class="activity-item activity-item-personal">
                    <span class="activity-icon"><span class="icon-placeholder icon-bath">🧼</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:00 AM - 10:45 AM</p>
                        <p class="activity-description">Levantarse y aseo 🧼 (Ducha y ropa limpia)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍳</span></span>
                    <div class="activity-content">
                        <p class="activity-time">10:45 AM - 11:30 AM</p>
                        <p class="activity-description">Desayuno 🍳 (Fruta variada con yogur)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">11:30 AM - 1:30 PM</p>
                        <p class="activity-description">Estudio 📚: Notas clave (2 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍽️</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:30 PM - 2:15 PM</p>
                        <p class="activity-description">Almuerzo 🍽️ (Cena liviana y fácil de digerir)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-snack">
                    <span class="activity-icon"><span class="icon-placeholder icon-apple">🍎</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:15 PM - 2:30 PM</p>
                        <p class="activity-description">Refrigerio 🍎 (Galletas de avena y un vaso de agua)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">2:30 PM - 4:45 PM</p>
                        <p class="activity-description">Estudio 📚: Plan de acción pre-examen (2.25 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-study">
                    <span class="activity-icon"><span class="icon-placeholder icon-book-red">📚</span></span>
                    <div class="activity-content">
                        <p class="activity-time">4:45 PM - 7:15 PM</p>
                        <p class="activity-description">Estudio 📚: Preguntas fáciles (2.5 hrs)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-film">🎥</span></span>
                    <div class="activity-content">
                        <p class="activity-time">7:15 PM - 8:00 PM</p>
                        <p class="activity-description">Juegos 🎥: Videos educativos ligeros o documentales de interés general 🍿</p>
                    </div>
                </div>
                <div class="activity-item activity-item-productivity">
                    <span class="activity-icon"><span class="icon-placeholder icon-lightbulb">✨</span></span>
                    <div class="activity-content">
                        <p class="activity-time">8:00 PM - 9:00 PM</p>
                        <p class="activity-description">Productividad ✨: Actividad libre ligera (meditación, estiramientos) y reflexión sobre el progreso 😌</p>
                    </div>
                </div>
                <div class="activity-item activity-item-meal">
                    <span class="activity-icon"><span class="icon-placeholder icon-utensils">🍜</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:00 PM - 9:45 PM</p>
                        <p class="activity-description">Cena 🍜 (Cena muy ligera)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-leisure">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">🎮</span></span>
                    <div class="activity-content">
                        <p class="activity-time">9:45 PM - 12:45 AM (sig. día)</p>
                        <p class="activity-description">Libre nocturno 🎮: Genshin/Roblox (actividad relajante)</p>
                    </div>
                </div>
                <div class="activity-item activity-item-sleep">
                    <span class="activity-icon"><span class="icon-placeholder icon-moon">😴</span></span>
                    <div class="activity-content">
                        <p class="activity-time">1:00 AM - 10:00 AM (sig. día)</p>
                        <p class="activity-description">Dormir 😴</p>
                    </div>
                </div>
            </div>
        </div>

    </div>
</body>
</html>
```
63.5s
