<!DOCTYPE html>
<!-- saved from url=(0070)file:///C:/Users/user/Desktop/mubti%20%ED%85%8C%EC%8A%A4%ED%8A%B8.html -->
<html lang="ko"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>뮤직 MBTI 테스트</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Arial', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            max-width: 600px;
            width: 100%;
            text-align: center;
        }
        
        .header {
            margin-bottom: 30px;
        }
        
        .header h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .header p {
            color: #666;
            font-size: 1.1em;
        }
        
        .question-container {
            margin-bottom: 30px;
            text-align: left;
        }
        
        .question {
            font-size: 1.3em;
            color: #333;
            margin-bottom: 20px;
            font-weight: bold;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .option {
            background: #f8f9fa;
            border: 2px solid #e9ecef;
            border-radius: 15px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 1.1em;
        }
        
        .option:hover {
            background: #e3f2fd;
            border-color: #2196f3;
            transform: translateY(-2px);
        }
        
        .option.selected {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border-color: #667eea;
        }
        
        .progress-bar {
            width: 100%;
            height: 10px;
            background: #e9ecef;
            border-radius: 5px;
            margin-bottom: 20px;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background: linear-gradient(45deg, #667eea, #764ba2);
            transition: width 0.3s ease;
            border-radius: 5px;
        }
        
        .btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 1.1em;
            cursor: pointer;
            transition: transform 0.3s ease;
            margin: 10px;
        }
        
        .btn:hover {
            transform: translateY(-2px);
        }
        
        .btn:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .result-container {
            text-align: center;
            padding: 20px;
        }
        
        .result-type {
            font-size: 3em;
            margin-bottom: 10px;
        }
        
        .result-code {
            font-size: 2.5em;
            color: #667eea;
            margin-bottom: 10px;
            font-weight: bold;
            letter-spacing: 3px;
            font-family: 'Courier New', monospace;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .result-name {
            font-size: 2em;
            color: #333;
            margin-bottom: 10px;
            font-weight: bold;
        }
        .result-description {
            font-size: 1.2em;
            color: #666;
            margin-bottom: 20px;
            line-height: 1.6;
        }
        
        .trait {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
            padding: 10px;
            background: white;
            border-radius: 10px;
        }
        
        .playlist {
            background: #e8f5e8;
            border-radius: 15px;
            padding: 20px;
            margin-top: 20px;
        }
        
        .playlist h3 {
            color: #2e7d32;
            margin-bottom: 15px;
        }
        
        .song-list {
            text-align: left;
        }
        
        .song {
            padding: 8px 0;
            border-bottom: 1px solid #c8e6c9;
        }
        
        .song:last-child {
            border-bottom: none;
        }
        
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎵 Mu-BTI 테스트 🎵</h1>
            <p>당신만의 음악 성향을 찾아보세요!</p>
        </div>

        <div id="test-container">
            <div class="progress-bar">
                <div class="progress" id="progress" style="width: 7.14286%;"></div>
            </div>
            
            <div class="question-container">
                <div class="question" id="question">🎵 좋아하는 음악의 멜로디는?</div>
                <div class="options" id="options"><div class="option">🎼 복잡하고 변화가 많은 멜로디</div><div class="option">📝 단순하고 기억하기 쉬운 멜로디</div><div class="option">🎶 높고 밝은 느낌의 멜로디</div><div class="option">💭 낮고 차분한 느낌의 멜로디</div></div>
            </div>
            
            <div style="text-align: center;">
                <button class="btn" id="prevBtn" onclick="prevQuestion()" disabled="">이전</button>
                <button class="btn" id="nextBtn" onclick="nextQuestion()" disabled="">다음</button>
            </div>
        </div>

        <div id="result-container" class="result-container hidden">
            <div class="result-type" id="resultType"></div>
            <div class="result-code" id="resultCode"></div>
            <div class="result-name" id="resultName"></div>
            <div class="result-description" id="resultDescription"></div>
            
            <div class="result-details">
                <h3>🎯 당신의 음악 성향</h3>
                <div id="traits"></div>
            </div>
            
            <div class="playlist">
                <h3>🎧 추천 플레이리스트</h3>
                <div class="song-list" id="playlist"></div>
            </div>
            
            <button class="btn" onclick="restartTest()">다시 테스트하기</button>
        </div>
    </div>

    <script>
        const questions = [
            {
                question: "🎵 좋아하는 음악의 멜로디는?",
                options: [
                    { text: "🎼 복잡하고 변화가 많은 멜로디", type: "C" },
                    { text: "📝 단순하고 기억하기 쉬운 멜로디", type: "S" },
                    { text: "🎶 높고 밝은 느낌의 멜로디", type: "G" },
                    { text: "💭 낮고 차분한 느낌의 멜로디", type: "Q" },

                ]
            },
            {
                question: "🌍 어떤 리듬을 좋아하나요?",
                options: [
                    { text: "🔥 빠르고 신나는 리듬", type: "F" },
                    { text: "🌙 느리고 여유로운 리듬", type: "S" },
                    { text: "🎶 복잡한 박자의 리듬", type: "C" },
                    { text: "💭 일정하고 안정적인 리듬", type: "S" },
                ]
            },
            {
                question: "🎤 노래에서 가장 중요한 것은?",
                options: [
                    { text: "🎵 감동적인 가사", type: "L" },
                    { text: "💭 아름다운 멜로디", type: "M" },
                    { text: "📝 가사와 멜로디 둘 다", type: "M" },

                ]
            },
            {
                question: "⚡ 어떤 악기 소기(음색)을 좋아하나요?",
                options: [
                    { text: "🔥 강렬하고 임팩트 있는 전자 악기 소리", type: "H" },
                    { text: "🌙 잔잔하고 감미로운 한 가지 악기 소리", type: "S" },
                    { text: " 🎵다양한 악기가 어우러져 화음이 조화로운 소리", type: "C" },
                    { text: " 🎤따뜻하고 부드러운 느낌의 소리", type: "Q" },
                ]
            },
            {
                question: "🏃‍♀️ 좋아하는 음악의 빠르기는?",
                options: [
                    { text: "💪 빠른 템포", type: "F" },
                    { text: "💭 중간 템포", type: "F" },
                    { text: "🧘‍♀️ 느린 템포", type: "S" },
                ]
            },
            {
                question: "😴 좋아하는 음악의 볼륨은?",
                options: [
                    { text: "🎵 크고 웅장한 소리", type: "H" },
                    { text: "🌜 작고 섬세한 소리", type: "Q" },
                    { text: "🎵 적당한 크기의 소리", type: "Q" },
                ]
            },
            {
                question: "🔊 음악을 들을 때 내가 집중하는 부분은?",
                options: [
                    { text: "📢 가사의 의미", type: "L" },
                    { text: "🔇 멜로디의 아름다움", type: "M" },
                    { text: "⚡ 박자감", type: "M" },
                    { text: "🔇 전체적인 느낌", type: "M" },
                ]
            },
            {
                question: "🎧 선호하는 음악 장르는?",
                options: [
                    { text: "🔊 K-POP, 팝, 댄스 등 신나는 음악", type: "F" },
                    { text: "🔊 발라드, 포크송 등 잔잔한 음악", type: "S" },
                    { text: "🔊 록, 힙합 등 강한 느낌의 음악", type: "H" },
                    { text: "🔊 클래식, 재즈 등 복잡한 화음의 음악", type: "C" },
                    { text: "👂 부담없이 들을 수 있는 이지리스닝 팝", type: "S" },
                ]
            },
            {
                question: "🎉 내가 음악을 들으며 하고 싶은 일은?",
                options: [
                    { text: "🎊 댄스댄스, 춤추기", type: "F" },
                    { text: "👥 친구들과 함께 듣기", type: "H" },
                    { text: "👥 방에서 조용히 감상하기", type: "Q" },
                    { text: "👥 노래 따라 부르기", type: "L" },
                ]
            },
            {
                question: "🎸 어떤 악기 소리(음색)를 좋아하나요?",
                options: [
                    { text: "🎸 기타 같은 반주 악기", type: "M" },
                    { text: "🎹 피아노같은 멜로디 악기", type: "M" },
                    { text: "🎊 드럼 같은 리듬 악기", type: "F" },
                    { text: "🎼 바이올린 같은 선율 악기", type: "C" },
                    { text: "👂 악기소리보다는 가수 목소리", type: "S" },
                ]
            },
            {
                question: "🎵 음악으로 얻어가고 싶은 감정은?",
                options: [
                    { text: "🎪 에너지와 힘", type: "F" },
                    { text: "🎪 위로와 치유", type: "S" },
                    { text: "🎪 감동과 깊이", type: "Q" },
                    { text: "🎪 즐거움과 신남", type: "H" },
                ]
            },
            {
                question: "🎚️ 내가 새로운 음악을 찾는 방법은?",
                options: [
                    { text: "🔄 친구 추천", type: "H" },
                    { text: "✨ 음악 차트 확인", type: "F" },
                    { text: "✨ 가사 검색", type: "L" },
                    { text: "✨ 기존 좋아하던 노래와 비슷한 스타일 찾기", type: "M" },
                ]
            },
            {
                question: "🎚️ 음악하면 떠오르는 색깔은?",
                options: [
                    { text: "빨강, 노랑 등 따뜻한 색", type: "H" },
                    { text: "파랑, 보라 등 차가운 색", type: "Q" },
                    { text: "무지개 색깔처럼 다양한 색", type: "C" },
                    { text: "검은색, 흰색처럼 단순한 색", type: "S" },
                ]
            },
            {
                question: "🎚️ 음악을 듣기 좋은 시간대는?",
                options: [
                    { text: "아침에 활기차게", type: "F" },
                    { text: "낮에 편안하게", type: "H" },
                    { text: "저녁에 여유롭게", type: "Q" },
                    { text: "자기 전에 깊이있게", type: "S" },
                ]
            },


        ];

        const musicTypes = {
            "MFHC": { name: "메가 멜로디 마스터", emoji: "🎼👑", description: "복잡하고 강렬한 멜로디의 대가! 빠르고 웅장한 음악을 사랑하는 당신은 음악의 모든 디테일을 놓치지 않아요." },
            "MFHS": { name: "캐치 멜로디 킹", emoji: "🎵⚡", description: "중독성 있는 멜로디 헌터! 빠르고 강렬하지만 심플한 멜로디로 모든 사람을 사로잡는 매력을 가졌어요." },
            "MFQC": { name: "멜로디 크래프터", emoji: "🎨🎼", description: "섬세한 멜로디 장인! 빠른 리듬 속에서도 복잡한 멜로디의 아름다움을 발견하는 예술가예요." },
            "MFQS": { name: "팝 멜로디 러버", emoji: "🌟🎵", description: "완벽한 팝 멜로디 애호가! 빠르고 깔끔한 멜로디로 언제나 기분을 UP시키는 당신!" },
            "MSHC": { name: "멜로디 몽환가", emoji: "🌙🎼", description: "깊고 복잡한 멜로디의 탐험가! 느리고 웅장한 멜로디 속에서 진정한 감동을 찾아요." },
            "MSHS": { name: "클래식 멜로디언", emoji: "🎭🎼", description: "우아한 멜로디의 감상가! 느리고 강렬한 멜로디로 깊은 감정을 표현하는 로맨티스트예요." },
            "MSQC": { name: "앰비언트 멜로디스트", emoji: "🌊🎵", description: "신비로운 멜로디의 탐구자! 조용하고 복잡한 멜로디로 내면의 세계를 탐험해요." },
            "MSQS": { name: "발라드 프린스/프린세스", emoji: "👑💝", description: "감성 멜로디의 왕자/공주! 조용하고 아름다운 멜로디로 마음을 울리는 당신!" },
            "LFHC": { name: "힙합 리리시스트", emoji: "🎤🔥", description: "파워풀한 가사의 전달자! 빠르고 강렬한 랩과 메시지로 세상을 바꾸고 싶어해요." },
            "LFHS": { name: "록 보컬리스트", emoji: "🤘🎸", description: "강렬한 가사의 록스타! 빠르고 파워풀한 메시지로 에너지를 폭발시키는 당신!" },
            "LFQC": { name: "마술사 음유시인", emoji: "✍️🎵", description: "섬세한 가사의 시인! 빠른 리듬 속에서도 복잡한 감정을 담아내는 예술가예요." },
            "LFQS": { name: "팝 송라이터", emoji: "📝✨", description: "완벽한 가사의 작가! 빠르고 간결한 메시지로 모든 이의 마음을 사로잡아요." },
            "LSHC": { name: "소울 스토리텔러", emoji: "🎭📖", description: "깊은 가사의 이야기꾼! 느리고 웅장한 음악으로 인생의 진리를 전달해요." },
            "LSHS": { name: "발라드 시인", emoji: "🌹📜", description: "감성 가사의 마에스트로! 느리고 강렬한 감정으로 사랑과 이별을 노래해요." },
            "LSQC": { name: "포크 철학자", emoji: "🍃💭", description: "사색적 가사의 현자! 조용하고 복잡한 메시지로 세상을 깊이 있게 바라봐요." },
            "LSQS": { name: "어쿠스틱 감성러", emoji: "🎸💖", description: "순수한 가사의 감성 메신저! 조용하고 진솔한 이야기로 마음을 따뜻하게 해요." }
        };

        const playlists = {
            "MFHC": ["데이식스 - 웰컴투더쇼", "빅뱅 - 뱅뱅뱅", "에스파 - 수퍼노바", "리스트 - 라 캄파넬라", "음율 - 파도혁명"],
            "MFHS": ["BOYNEXTDOOR - I feel good", "정국 - seven", "동요 - 우유송", "리센느 - 러브어택", "Maroon5 - payphone"],
            "MFQC": ["전영호 - Butterfly", "이무진 - 청춘만화", "음율 - 피차일반", "young kai - blue", "히사이시 조 - Summer"],
            "MFQS": ["10cm - 너에게 닿기를", "황가람 - 반딧불", "Unikid - 분홍빛 밤에", "데이식스 - Maybe tomorrow", "Ugonna Onyekwe - Inescapable"],
            "MSHC": ["Woodz - Drowning", "비오 - 리무진", "유정석 - 질풍가도", "Boa - Duvet", "쿨 - 애상"],
            "MSHS": ["빅뱅 - 붉은 노을", "로제 - 아파트", "이승윤 - 정말다행이군", "최재림 - 거인을 데려와", "홍광호 - 지금 이 순간"],
            "MSQC": ["도시아이들 - 달빛창가에서", "잭 - 밤을 달리다", "BOYNEXTDOOR - 돌멩이", "DAY6 - 한 페이지가 될 수 있게", "AKMU - LoveLee"],
            "MSQS": ["황가람 - 반딧불", "이무진 - 청춘만화", "성진 - 나무는 결국 겨울을 견뎌낼 거야", "동요 - 곰세마리", "혁오 - tomboy"],
            "LFHC": ["이무진 - 뱁새", "체리필터 - 낭만고양이", "비오 - 리무진", "비와이 - 가라사대", "이무진 - 청춘만화"],
            "LFHS": ["데이식스 - 한 페이지가 될 수 있게", "악뮤 - 후라이의 꿈", "이승윤 - 여백한켠에", "넬 - 기억을 걷는 시간", "음율 - 파도혁명"],
            "LFQC": ["슈베르트 - 마왕", "홍광호 - 지금 이 순간", "10cm - 너에게 닿기를", "BOYNEXTDOOR - 돌멩이", "잔나비 - 주저하는 연인들을 위해"],
            "LFQS": ["로제 - 아파트", "BOYNEXTDOOR - 오늘만 i love you", "윤하 - 혜성", "10cm - 그라데이션", "동요 - 바라밤"],
            "LSHC": ["이무진 - 뱁새", "최재림 - 거인을 데려와", "슈베르트 - 마왕", "아이유 - 너의 의미", "신문희 - 아름다운 나라"],
            "LSHS": ["태연 - I", "10cm - 너에게 닿기를", "혁오 - tomboy", "아이유 - 밤편지", "The Beatles - Let It Be"],
            "LSQC": ["동요 - 섬집아기", "음율 - 파도혁명", "young kai - blue", "BOYNEXTDOOR - 돌멩이", "패닉 - 달팽이"],
            "LSQS": ["자두 - 김밥", "아이츠노유니 - 내꺼하는법", "BOYNEXTDOOR - I feel good", "로제 - 아파트", "동요 - 곰 세마리"]
        };

        let currentQuestion = 0;
        let answers = [];
        let scores = { M: 0, L: 0, F: 0, S: 0, H: 0, Q: 0, C: 0, S: 0 };

        function displayQuestion() {
            const question = questions[currentQuestion];
            document.getElementById('question').textContent = question.question;
            
            const optionsContainer = document.getElementById('options');
            optionsContainer.innerHTML = '';
            
            question.options.forEach((option, index) => {
                const div = document.createElement('div');
                div.className = 'option';
                div.textContent = option.text;
                div.onclick = () => selectOption(index);
                optionsContainer.appendChild(div);
            });
            
            updateProgress();
            updateButtons();
        }

        function selectOption(index) {
            const options = document.querySelectorAll('.option');
            options.forEach(opt => opt.classList.remove('selected'));
            options[index].classList.add('selected');
            
            answers[currentQuestion] = index;
            document.getElementById('nextBtn').disabled = false;
        }

        function nextQuestion() {
            if (answers[currentQuestion] === undefined) return;
            
            const question = questions[currentQuestion];
            const selectedOption = question.options[answers[currentQuestion]];
            scores[selectedOption.type]++;
            
            currentQuestion++;
            
            if (currentQuestion < questions.length) {
                displayQuestion();
            } else {
                showResult();
            }
        }

        function prevQuestion() {
            if (currentQuestion > 0) {
                currentQuestion--;
                displayQuestion();
            }
        }

        function updateProgress() {
            const progress = ((currentQuestion + 1) / questions.length) * 100;
            document.getElementById('progress').style.width = progress + '%';
        }

        function updateButtons() {
            document.getElementById('prevBtn').disabled = currentQuestion === 0;
            document.getElementById('nextBtn').disabled = answers[currentQuestion] === undefined;
        }

        function calculateResult() {
            let result = '';
            result += scores.M >= scores.L ? 'M' : 'L';
            result += scores.F >= scores.S ? 'F' : 'S';
            result += scores.H >= scores.Q ? 'H' : 'Q';
            result += scores.C >= scores.S ? 'C' : 'S';
            return result;
        }

        function showResult() {
            const resultType = calculateResult();
            const type = musicTypes[resultType];
            
            document.getElementById('test-container').classList.add('hidden');
            document.getElementById('result-container').classList.remove('hidden');
            
            document.getElementById('resultType').textContent = type.emoji;
            document.getElementById('resultCode').textContent = resultType;
            document.getElementById('resultName').textContent = type.name;
            document.getElementById('resultDescription').textContent = type.description;
            
            // 성향 표시
            const traits = [
                { name: '멜로디(Melody) vs 가사(Lyrics)', value: scores.M >= scores.L ? '멜로디 중심 (M)' : '가사 중심 (L)' },
                { name: '템포', value: scores.F >= scores.S ? '빠른 템포 (Fast)' : '느린 템포 (Slow)' },
                { name: '볼륨', value: scores.H >= scores.Q ? '강한 음량 (High)' : '적당한 음량 (Quiet)' },
                { name: '구성', value: scores.C >= scores.S ? '복잡한 편곡 (Complex)' : '심플한 편곡 (Simple)' }
            ];
            
            const traitsContainer = document.getElementById('traits');
            traitsContainer.innerHTML = '';
            traits.forEach(trait => {
                const div = document.createElement('div');
                div.className = 'trait';
                div.innerHTML = `<strong>${trait.name}:</strong> <span>${trait.value}</span>`;
                traitsContainer.appendChild(div);
            });
            
            // 플레이리스트 표시
            const playlistContainer = document.getElementById('playlist');
            playlistContainer.innerHTML = '';
            playlists[resultType].forEach(song => {
                const div = document.createElement('div');
                div.className = 'song';
                div.textContent = `🎵 ${song}`;
                playlistContainer.appendChild(div);
            });
        }

        function restartTest() {
            currentQuestion = 0;
            answers = [];
            scores = { M: 0, L: 0, F: 0, S: 0, H: 0, Q: 0, C: 0, S: 0 };
            
            document.getElementById('test-container').classList.remove('hidden');
            document.getElementById('result-container').classList.add('hidden');
            
            displayQuestion();
        }

        // 초기 실행
        displayQuestion();
    </script>

</body></html>
