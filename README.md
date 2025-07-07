# test-1
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار التحفيز - استبيان تقييم الدافعية</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            direction: rtl;
            line-height: 1.6;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .header h1 {
            color: #333;
            font-size: 2.5em;
            margin-bottom: 15px;
            font-weight: bold;
        }

        .header p {
            color: #666;
            font-size: 1.1em;
            margin-bottom: 20px;
        }

        .back-btn {
            background: #6c757d;
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
            margin-left: 10px;
        }

        .back-btn:hover {
            background: #5a6268;
        }

        .questionnaire {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            margin-bottom: 30px;
        }

        .question {
            margin-bottom: 25px;
            padding: 20px;
            background: #f8f9fa;
            border-radius: 10px;
            border-right: 4px solid #007bff;
        }

        .question-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }

        .question-number {
            background: #007bff;
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            margin-left: 15px;
        }

        .question-text {
            flex: 1;
            font-weight: bold;
            color: #333;
            font-size: 1.1em;
        }

        .options {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .option {
            background: white;
            border: 2px solid #ddd;
            border-radius: 10px;
            padding: 15px;
            cursor: pointer;
            transition: all 0.3s;
            min-width: 120px;
            text-align: center;
            font-weight: bold;
        }

        .option:hover {
            border-color: #007bff;
            box-shadow: 0 2px 10px rgba(0,123,255,0.2);
        }

        .option.selected {
            background: #007bff;
            color: white;
            border-color: #007bff;
        }

        .option-label {
            font-size: 0.9em;
            margin-bottom: 5px;
        }

        .option-value {
            font-size: 1.1em;
            font-weight: bold;
        }

        .submit-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 15px 40px;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            display: block;
            margin: 30px auto;
            transition: transform 0.3s;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
        }

        .submit-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }

        .results {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            margin-top: 30px;
        }

        .results h2 {
            color: #333;
            text-align: center;
            margin-bottom: 30px;
            font-size: 2em;
        }

        .chart-container {
            background: #f8f9fa;
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 20px;
        }

        .chart-title {
            font-weight: bold;
            margin-bottom: 10px;
            color: #333;
        }

        .chart-bar {
            display: flex;
            align-items: center;
            margin-bottom: 10px;
        }

        .chart-label {
            width: 120px;
            font-weight: bold;
            color: #666;
            margin-left: 10px;
        }

        .chart-progress {
            flex: 1;
            height: 25px;
            background: #e0e0e0;
            border-radius: 12px;
            overflow: hidden;
            margin-left: 10px;
        }

        .chart-fill {
            height: 100%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 12px;
            transition: width 0.5s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .summary-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }

        .summary-table th,
        .summary-table td {
            padding: 12px;
            text-align: center;
            border: 1px solid #ddd;
        }

        .summary-table th {
            background: #f8f9fa;
            font-weight: bold;
        }

        .graph-container {
            margin-top: 30px;
            background: white;
            padding: 30px;
            border-radius: 10px;
            border: 2px solid #333;
            position: relative;
        }

        .graph-title {
            font-weight: bold;
            margin-bottom: 30px;
            color: #333;
            text-align: center;
            font-size: 1.4em;
        }

        .graph-grid {
            border: 2px solid #333;
            background: white;
            position: relative;
        }

        .graph-header {
            display: grid;
            grid-template-columns: 120px repeat(13, 1fr);
            border-bottom: 2px solid #333;
            background: #f8f9fa;
        }

        .graph-header div {
            padding: 8px 4px;
            text-align: center;
            font-weight: bold;
            font-size: 12px;
            border-left: 1px solid #333;
        }

        .graph-header div:first-child {
            border-left: none;
            background: #f8f9fa;
        }

        .graph-row {
            display: grid;
            grid-template-columns: 120px repeat(13, 1fr);
            border-bottom: 1px solid #333;
            min-height: 40px;
            position: relative;
        }

        .graph-row:last-child {
            border-bottom: none;
        }

        .category-label {
            font-weight: bold;
            color: #333;
            padding: 10px 8px;
            display: flex;
            align-items: center;
            font-size: 13px;
            border-left: 2px solid #333;
            background: #f8f9fa;
        }

        .score-cell {
            border-left: 1px solid #333;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
        }

        .score-cell:first-of-type {
            border-left: none;
        }

        .score-point {
            width: 8px;
            height: 8px;
            background: #000;
            border-radius: 50%;
            position: relative;
            z-index: 2;
        }

        .connecting-line {
            position: absolute;
            height: 2px;
            background: #000;
            top: 50%;
            transform: translateY(-50%);
            z-index: 1;
        }

        .zero-line {
            background: #666 !important;
        }

        .zero-cell {
            background: #f0f0f0 !important;
        }

        .hidden {
            display: none;
        }

        .success-message {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
            padding: 10px;
            border-radius: 5px;
            margin: 10px 0;
            text-align: center;
            font-weight: bold;
        }

        @media (max-width: 768px) {
            .options {
                flex-direction: column;
            }
            
            .option {
                min-width: auto;
            }
            
            .header h1 {
                font-size: 2em;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>اختبار التحفيز</h1>
            <p>ما الذي تعتقد أنه يحفز الناس على الأداء بشكل جيد؟</p>
            <p>تم تصميم هذا الاستبيان ليختبر مواقفك ومعتقداتك حول التحفيز. كل من العبارات المقابلة لها إجابات محتملة.</p>
        </div>

        <div class="questionnaire" id="questionnaire">
            <!-- Questions will be populated by JavaScript -->
        </div>

        <div class="results hidden" id="results">
            <h2>نتائج الاختبار</h2>

            <div class="summary-table-container">
                <table class="summary-table">
                    <thead>
                        <tr>
                            <th>الفئة</th>
                            <th>النقاط</th>
                        </tr>
                    </thead>
                    <tbody id="summaryTableBody"></tbody>
                </table>
            </div>
            
            <div class="graph-container">
                <div class="graph-title">الرسم البياني للنتائج</div>
                <div class="graph-grid">
                    <div class="graph-header">
                        <div>الدرجة</div>
                        <div>6-</div>
                        <div>5-</div>
                        <div>4-</div>
                        <div>3-</div>
                        <div>2-</div>
                        <div>1-</div>
                        <div class="zero-cell">0</div>
                        <div>1+</div>
                        <div>2+</div>
                        <div>3+</div>
                        <div>4+</div>
                        <div>5+</div>
                        <div>6+</div>
                    </div>
                    <div id="graphLines"></div>
                </div>
            </div>

            <div class="action-controls">
                <button class="back-btn" onclick="goBackToQuestions()">العودة للاختبار</button>
            </div>
        </div>
    </div>

    <script>
        const questions = [
            "المال هو حقاً الطريقة الوحيدة للتحفيز على الأداء الجيد",
            "أغلب الناس يؤدون بشكل أفضل عندما يدركون مديرهم إنهم قد يفقدون وظائفهم إذا لم يعملوا بكفاءة ويساعدوا في استمرار الحركة في المنافسة",
            "أراء الموظفين عملهم بشكل جيد يعتمد إلى حد كبير على بيئة عملهم",
            "الشعور بالانتماء لمجموعة تنتمي لفريق قوي هو عامل مهم في التحفيز الإنساني",
            "التقدير الشخصي للأداء، فوق المتوسط أكثر أهمية للناس من المال",
            "تقديم خطة تقاعد وميزات مرضية جيدة هي أساليب جيدة لتحفيز أغلب الناس",
            "بعض الموظفين يفضلون العمل بمفردهم بدون مساعدة في مشروع صعب على العمل في مجموعة",
            "التقدير على المشاركة في الأحداث الاجتماعية التي يتم تطبيقها في العمل تجعل الناس على العمل بشكل جيد",
            "التفخر الشخصي بالإنجازات أكثر أهمية بالنسبة لمعظم الناس من تهاني الرؤساء والزملاء",
            "بوجه عام، يؤدي الموظفون بشكل جيد عندما يعرفون أن الآخرين يعرفون أكثر مهارة من زملائهم في جزء ما من عملهم",
            "جودة العلاقات في مجموعات العمل غير الرسمية مهم ولكن تحفيز الأفراد على العمل بشكل جيد",
            "رؤية عمل الموظفين وتقديره وإحساسهم من قبل الإدارة العليا هو محفز كبير لمعظم الناس",
            "معظم الموظفين يرحبون بفرصة العمل بمفردهم واتخاذ القرارات بدون إشراف",
            "معظم الناس هذه الأيام مستعدون للعمل بجد وبشكل جيد لمجرد أنهم سعداء بالحصول على وظيفة",
            "حتى عندما يحب الناس عملهم، فإن الطريقة الوحيدة لتحفيزهم على الأداء، بشكل أفضل في حتى أن تقدم لهم أدوات وتجهيزات أفضل"
        ];

        const optionLabels = [
            { text: "أتفق بشدة", value: 2 },
            { text: "أتفق", value: 1 },
            { text: "لا أتفق ولا أختلف", value: 0 },
            { text: "أختلف", value: -1 },
            { text: "أختلف بشدة", value: -2 }
        ];

        const categories = {
            "إشباع الذات": [1, 5, 9, 13],
            "الأمان": [2, 6, 10, 14],
            "الانتماء": [3, 7, 11, 15],
            "الاحترام": [4, 8, 12],
            "المادية": [1, 3, 5, 7]
        };

        let responses = {};

        function initializeSurvey() {
            generateQuestions();
            loadResponses();
        }

        function generateQuestions() {
            const container = document.getElementById('questionnaire');
            container.innerHTML = '';

            questions.forEach((question, index) => {
                const questionDiv = document.createElement('div');
                questionDiv.className = 'question';
                questionDiv.innerHTML = `
                    <div class="question-header">
                        <div class="question-number">${index + 1}</div>
                        <div class="question-text">${question}</div>
                    </div>
                    <div class="options">
                        ${optionLabels.map(option => `
                            <div class="option" onclick="selectOption(${index + 1}, ${option.value})">
                                <div class="option-label">${option.text}</div>
                                <div class="option-value">${option.value > 0 ? '+' : ''}${option.value}</div>
                            </div>
                        `).join('')}
                    </div>
                `;
                container.appendChild(questionDiv);
            });

            const submitBtn = document.createElement('button');
            submitBtn.className = 'submit-btn';
            submitBtn.textContent = 'عرض النتائج';
            submitBtn.onclick = showResults;
            container.appendChild(submitBtn);
        }

        function selectOption(questionIndex, value) {
            responses[questionIndex] = value;
            saveResponses();
            
            // Update UI
            const questionDiv = document.querySelector(`.question:nth-child(${questionIndex})`);
            const options = questionDiv.querySelectorAll('.option');
            
            options.forEach((option, index) => {
                option.classList.remove('selected');
                if (optionLabels[index].value === value) {
                    option.classList.add('selected');
                }
            });
        }

        function showResults() {
            const totalQuestions = questions.length;
            const answeredQuestions = Object.keys(responses).length;
            
            if (answeredQuestions < totalQuestions) {
                alert(`يرجى الإجابة على جميع الأسئلة (${answeredQuestions}/${totalQuestions})`);
                return;
            }

            calculateResults();
            document.getElementById('questionnaire').classList.add('hidden');
            document.getElementById('results').classList.remove('hidden');
        }

        function calculateResults() {
            const categoryScores = {};
            const maxScores = {};
            
            // Initialize scores
            Object.keys(categories).forEach(category => {
                categoryScores[category] = 0;
                maxScores[category] = categories[category].length * 2; // Maximum possible score
            });

            // Calculate scores for each category
            Object.keys(categories).forEach(category => {
                categories[category].forEach(questionIndex => {
                    if (responses[questionIndex] !== undefined) {
                        categoryScores[category] += responses[questionIndex];
                    }
                });
            });

            displayLineGraph(categoryScores);
            displaySummaryTable(categoryScores, maxScores);
        }

        function displayLineGraph(scores) {
            const graphLines = document.getElementById('graphLines');
            graphLines.innerHTML = '';

            const categories = ['إشباع الذات', 'الأمان', 'الانتماء', 'الاحترام', 'المادية'];
            const scoreValues = [-6, -5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5, 6];
            const scorePositions = {};

            categories.forEach((category, categoryIndex) => {
                const score = scores[category] || 0;
                scorePositions[category] = score;
                
                const rowDiv = document.createElement('div');
                rowDiv.className = 'graph-row';
                
                // Category label
                const categoryLabel = document.createElement('div');
                categoryLabel.className = 'category-label';
                categoryLabel.textContent = category;
                rowDiv.appendChild(categoryLabel);
                
                // Score cells
                scoreValues.forEach((value, index) => {
                    const cell = document.createElement('div');
                    cell.className = 'score-cell';
                    
                    if (value === 0) {
                        cell.classList.add('zero-cell');
                    }
                    
                    if (value === score) {
                        const point = document.createElement('div');
                        point.className = 'score-point';
                        cell.appendChild(point);
                    }
                    
                    rowDiv.appendChild(cell);
                });
                
                graphLines.appendChild(rowDiv);
            });

            // Draw connecting lines after all points are placed
            setTimeout(() => {
                drawConnectingLines(scorePositions, scoreValues);
            }, 100);
        }

        function drawConnectingLines(scorePositions, scoreValues) {
            const rows = document.querySelectorAll('.graph-row');
            const categories = ['إشباع الذات', 'الأمان', 'الانتماء', 'الاحترام', 'المادية'];
            
            // Clear any existing lines
            document.querySelectorAll('.connecting-line').forEach(line => line.remove());
            
            for (let i = 0; i < categories.length - 1; i++) {
                const currentCategory = categories[i];
                const nextCategory = categories[i + 1];
                
                const currentScore = scorePositions[currentCategory];
                const nextScore = scorePositions[nextCategory];
                
                const currentRow = rows[i];
                const nextRow = rows[i + 1];
                
                // Find the position of current score in the grid
                const currentScoreIndex = scoreValues.indexOf(currentScore);
                const nextScoreIndex = scoreValues.indexOf(nextScore);
                
                if (currentScoreIndex !== -1 && nextScoreIndex !== -1) {
                    const currentCell = currentRow.children[currentScoreIndex + 1]; // +1 because first cell is label
                    const nextCell = nextRow.children[nextScoreIndex + 1];
                    
                    if (currentCell && nextCell) {
                        const line = document.createElement('div');
                        line.className = 'connecting-line';
                        
                        // Calculate line position and dimensions
                        const currentRect = currentCell.getBoundingClientRect();
                        const nextRect = nextCell.getBoundingClientRect();
                        const containerRect = currentRow.getBoundingClientRect();
                        
                        const currentCenterX = currentRect.left + currentRect.width / 2 - containerRect.left;
                        const nextCenterX = nextRect.left + nextRect.width / 2 - containerRect.left;
                        
                        const deltaX = nextCenterX - currentCenterX;
                        const deltaY = nextRect.top - currentRect.top;
                        
                        const length = Math.sqrt(deltaX * deltaX + deltaY * deltaY);
                        const angle = Math.atan2(deltaY, deltaX) * 180 / Math.PI;
                        
                        line.style.width = length + 'px';
                        line.style.left = currentCenterX + 'px';
                        line.style.top = '50%';
                        line.style.transform = `translateY(-50%) rotate(${angle}deg)`;
                        line.style.transformOrigin = '0 50%';
                        
                        currentRow.appendChild(line);
                    }
                }
            }
        }

        function displaySummaryTable(scores, maxScores) {
            const tableBody = document.getElementById('summaryTableBody');
            tableBody.innerHTML = '';

            Object.keys(scores).forEach(category => {
                const score = scores[category];

                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${category}</td>
                    <td>${score > 0 ? '+' : ''}${score}</td>
                `;
                tableBody.appendChild(row);
            });
        }

        function goBackToQuestions() {
            document.getElementById('results').classList.add('hidden');
            document.getElementById('questionnaire').classList.remove('hidden');
            
            // Restore the selected answers in the UI
            restoreSelectedAnswers();
        }

        function restoreSelectedAnswers() {
            Object.keys(responses).forEach(questionIndex => {
                const value = responses[questionIndex];
                const questionDiv = document.querySelector(`.question:nth-child(${questionIndex})`);
                if (questionDiv) {
                    const options = questionDiv.querySelectorAll('.option');
                    options.forEach((option, index) => {
                        option.classList.remove('selected');
                        if (optionLabels[index].value === value) {
                            option.classList.add('selected');
                        }
                    });
                }
            });
        }

        function saveResponses() {
            // In a real application, you would save to localStorage or send to server
            // For now, we'll just log the responses
            console.log('Responses saved:', responses);
        }

        function loadResponses() {
            // In a real application, you would load from localStorage or server
            // For now, we'll start with empty responses
            responses = {};
        }

        // Initialize the survey when the page loads
        window.onload = initializeSurvey;
    </script>
</body>
</html>
