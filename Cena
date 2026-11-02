<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Un Natale da leonesse</title>
    <script src="https://cdn.jsdelivr.net/npm/react@18/umd/react.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@babel/standalone@7/babel.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,600;0,700;1,400&family=Plus+Jakarta+Sans:wght@400;500;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-burgundy: #4A1525;
            --bg-card: #FAF6F0;
            --accent-gold: #D4AF37;
            --text-dark: #331A22;
        }
        body {
            background-color: var(--bg-burgundy);
            font-family: 'Plus Jakarta Sans', sans-serif;
            color: var(--text-dark);
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            min-height: 100vh;
        }
        .container {
            width: 100%;
            max-width: 440px;
            background: var(--bg-card);
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
            box-shadow: 0 0 30px rgba(0,0,0,0.5);
            position: relative;
        }
        h1, h2, h3 {
            font-family: 'Playfair Display', serif;
        }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        function App() {
            const [nickname, setNickname] = React.useState('');
            const [selectedDates, setSelectedDates] = React.useState([]);
            const [activeTab, setActiveTab] = React.useState('voto');
            const [allVotes, setAllVotes] = React.useState([
                { name: "Elena 🌸", dates: ["2026-11-20", "2026-11-21", "2026-12-04", "2026-12-18", "2026-12-19"] },
                { name: "Martina ✨", dates: ["2026-12-04", "2026-12-05", "2026-12-11", "2026-12-12", "2026-12-18"] },
                { name: "Sofia 🎄", dates: ["2026-11-27", "2026-11-28", "2026-12-18", "2026-12-19"] },
                { name: "Chiara 🥂", dates: ["2026-12-04", "2026-12-05", "2026-12-12", "2026-12-18", "2026-12-19"] }
            ]);

            // Generazione giorni dal 15 Novembre al 24 Dicembre 2026
            const generateDays = () => {
                let days = [];
                // Novembre 2026: dal 15 al 30
                for (let d = 15; d <= 30; d++) {
                    days.push({ date: `2026-11-${d < 10 ? '0'+d : d}`, dayNum: d, month: 'Novembre 2026', isWeekend: (new Date(2026, 10, d).getDay() === 5 || new Date(2026, 10, d).getDay() === 6) });
                }
                // Dicembre 2026: dal 1 al 24
                for (let d = 1; d <= 24; d++) {
                    days.push({ date: `2026-12-${d < 10 ? '0'+d : d}`, dayNum: d, month: 'Dicembre 2026', isWeekend: (new Date(2026, 11, d).getDay() === 5 || new Date(2026, 11, d).getDay() === 6) });
                }
                return days;
            };

            const daysList = generateDays();

            const toggleDate = (dateStr) => {
                if (selectedDates.includes(dateStr)) {
                    setSelectedDates(selectedDates.filter(d => d !== dateStr));
                } else {
                    setSelectedDates([...selectedDates, dateStr]);
                }
            };

            const handleSave = () => {
                if (!nickname.trim()) {
                    alert("Inserisci prima il tuo nome o nickname!");
                    return;
                }
                if (selectedDates.length === 0) {
                    alert("Seleziona almeno un giorno in cui sei libera!");
                    return;
                }
                // Salva o aggiorna i voti
                const filtered = allVotes.filter(v => v.name.toLowerCase() !== nickname.trim().toLowerCase());
                setAllVotes([...filtered, { name: nickname.trim(), dates: selectedDates }]);
                setActiveTab('riepilogo');
            };

            return (
                <div style={{ paddingBottom: '40px' }}>
                    {/* Header decorato */}
                    <div style={{ textAlign: 'center', marginBottom: '20px' }}>
                        <div style={{ fontSize: '28px', marginBottom: '5px' }}>🦁🎄🥂</div>
                        <h1 style={{ color: '#4A1525', margin: '0 0 5px 0', fontSize: '26px' }}>Un Natale da leonesse</h1>
                        <p style={{ fontStyle: 'italic', color: '#774C58', fontSize: '14px', margin: 0 }}>
                            Mamme in libera uscita: scegliamo la data!<br/>
                            Solo per noi, branco femminile • dal 15 novembre al 24 dicembre
                        </p>
                    </div>

                    {/* Tabs */}
                    <div style={{ display: 'flex', background: '#EAD7CD', borderRadius: '12px', padding: '4px', marginBottom: '20px' }}>
                        <button 
                            onClick={() => setActiveTab('voto')}
                            style={{ flex: 1, padding: '10px', border: 'none', background: activeTab === 'voto' ? '#FAF6F0' : 'transparent', borderRadius: '10px', fontWeight: 'bold', cursor: 'pointer', color: '#4A1525' }}>
                            🎁 Voto io
                        </button>
                        <button 
                            onClick={() => setActiveTab('riepilogo')}
                            style={{ flex: 1, padding: '10px', border: 'none', background: activeTab === 'riepilogo' ? '#FAF6F0' : 'transparent', borderRadius: '10px', fontWeight: 'bold', cursor: 'pointer', color: '#4A1525' }}>
                            🏆 Riepilogo
                        </button>
                    </div>

                    {activeTab === 'voto' ? (
                        <div>
                            <h3 style={{ color: '#4A1525', marginBottom: '8px' }}>🦁 Quando sei libera?</h3>
                            <label style={{ fontSize: '13px', fontWeight: '600', color: '#555' }}>Il tuo nome o nickname</label>
                            <input 
                                type="text" 
                                placeholder="es. Mamma Leonessa" 
                                value={nickname}
                                onChange={(e) => setNickname(e.target.value)}
                                style={{ width: '100%', padding: '12px', marginTop: '5px', marginBottom: '15px', borderRadius: '8px', border: '1px solid #D4AF37', boxSizing: 'border-box', background: '#fff' }}
                            />
                            <p style={{ fontSize: '12px', color: '#666', marginBottom: '15px' }}>
                                Tocca tutti i giorni in cui puoi esserci. Venerdì e sabato hanno il bordo dorato ✨
                            </p>

                            {/* Griglia Novembre */}
                            <h4 style={{ color: '#2C5E3B', margin: '15px 0 8px 0' }}>Novembre 2026</h4>
                            <div style={{ display: 'grid', gridTemplateColumns: 'repeat(7, 1fr)', gap: '6px', marginBottom: '15px' }}>
                                {['L','M','M','G','V','S','D'].map((d, i) => <div key={i} style={{ textAlign: 'center', fontSize: '11px', fontWeight: 'bold', color: '#888' }}>{d}</div>)}
                                {daysList.filter(d => d.month.includes('Novembre')).map((item, idx) => {
                                    const isSelected = selectedDates.includes(item.date);
                                    return (
                                        <div 
                                            key={idx}
                                            onClick={() => toggleDate(item.date)}
                                            style={{
                                                aspectRatio: '1',
                                                display: 'flex',
                                                alignItems: 'center',
                                                justifyContent: 'center',
                                                borderRadius: '8px',
                                                fontSize: '14px',
                                                fontWeight: '600',
                                                cursor: 'pointer',
                                                background: isSelected ? '#4A1525' : '#fff',
                                                color: isSelected ? '#fff' : '#331A22',
                                                border: item.isWeekend ? '2px solid #D4AF37' : '1px solid #E0D0C5'
                                            }}
                                        >
                                            {item.dayNum}
                                        </div>
                                    );
                                })}
                            </div>

                            {/* Griglia Dicembre */}
                            <h4 style={{ color: '#2C5E3B', margin: '20px 0 8px 0' }}>Dicembre 2026</h4>
                            <div style={{ display: 'grid', gridTemplateColumns: 'repeat(7, 1fr)', gap: '6px', marginBottom: '20px' }}>
                                {['L','M','M','G','V','S','D'].map((d, i) => <div key={i} style={{ textAlign: 'center', fontSize: '11px', fontWeight: 'bold', color: '#888' }}>{d}</div>)}
                                {daysList.filter(d => d.month.includes('Dicembre')).map((item, idx) => {
                                    const isSelected = selectedDates.includes(item.date);
                                    return (
                                        <div 
                                            key={idx}
                                            onClick={() => toggleDate(item.date)}
                                            style={{
                                                aspectRatio: '1',
                                                display: 'flex',
                                                alignItems: 'center',
                                                justifyContent: 'center',
                                                borderRadius: '8px',
                                                fontSize: '14px',
                                                fontWeight: '600',
                                                cursor: 'pointer',
                                                background: isSelected ? '#4A1525' : '#fff',
                                                color: isSelected ? '#fff' : '#331A22',
                                                border: item.isWeekend ? '2px solid #D4AF37' : '1px solid #E0D0C5'
                                            }}
                                        >
                                            {item.dayNum}
                                        </div>
                                    );
                                })}
                            </div>

                            <button 
                                onClick={handleSave}
                                style={{ width: '100%', padding: '14px', background: '#4A1525', color: '#FAF6F0', border: 'none', borderRadius: '10px', fontSize: '16px', fontWeight: 'bold', cursor: 'pointer', boxShadow: '0 4px 10px rgba(0,0,0,0.2)' }}>
                                ✨ Salva le mie disponibilità
                            </button>
                        </div>
                    ) : (
                        <div>
                            <h3 style={{ color: '#4A1525', marginBottom: '15px' }}>🏆 Classifica Date & Disponibili</h3>
                            {daysList.map(item => {
                                const availableUsers = allVotes.filter(v => v.dates.includes(item.date));
                                if (availableUsers.length === 0) return null;
                                return (
                                    <div key={item.date} style={{ background: '#fff', padding: '12px', borderRadius: '10px', marginBottom: '10px', border: '1px solid #E0D0C5' }}>
                                        <div style={{ fontWeight: 'bold', color: '#4A1525', display: 'flex', justifyContent: 'space-between' }}>
                                            <span>{item.dayNum} {item.month.split(' ')[0]}</span>
                                            <span style={{ color: '#D4AF37' }}>⭐ {availableUsers.length} voti</span>
                                        </div>
                                        <div style={{ fontSize: '13px', color: '#555', marginTop: '5px' }}>
                                            {availableUsers.map(u => u.name).join(', ')}
                                        </div>
                                    </div>
                                );
                            })}
                        </div>
                    )}
                </div>
            );
        }
        ReactDOM.render(<App />, document.getElementById('root'));
    </script>
</body>
</html>
