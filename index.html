<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>UnHolyPatriarch's Gothic 1 Remake Lockpick Solver</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #1e1e1e;
            color: #d4d4d4;
            padding: 20px;
            max-width: 950px;
            margin: auto;
        }
        h2 {
            color: #569cd6;
            border-bottom: 1px solid #333;
            padding-bottom: 10px;
        }
        .controls {
            margin-bottom: 20px;
            background: #252526;
            padding: 15px;
            border-radius: 5px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
        }
        label {
            margin-right: 10px;
            font-weight: bold;
        }
        input[type="number"], select {
            background-color: #3c3c3c;
            color: #d4d4d4;
            border: 1px solid #555;
            padding: 5px;
            border-radius: 3px;
        }
        input[type="number"] {
            width: 60px;
        }
        select {
            width: 95px;
        }
        button {
            background-color: #0e639c;
            color: white;
            border: none;
            padding: 8px 15px;
            cursor: pointer;
            border-radius: 3px;
            font-weight: bold;
            transition: background-color 0.2s;
        }
        button:hover {
            background-color: #1177bb;
        }
        table {
            border-collapse: collapse;
            margin-top: 20px;
            width: 100%;
        }
        th, td {
            border: 1px solid #444;
            padding: 10px;
            text-align: center;
        }
        th {
            background-color: #2d2d30;
            color: #4fc1ff;
        }
        td input {
            width: 60px;
            text-align: center;
        }
        td select {
            width: 95px;
            text-align: center;
        }
        .hard-set {
            background-color: #252526 !important;
            color: #4fc1ff !important;
            border: 1px solid #252526 !important;
            font-weight: bold;
            cursor: not-allowed;
            appearance: none;
            -webkit-appearance: none;
            -moz-appearance: none;
        }
        .sub-label {
            font-size: 0.85em;
            font-weight: normal;
            color: #a0a0a0;
            display: block;
            margin-top: 4px;
        }
        .output-container {
            margin-top: 25px;
            padding: 15px;
            background: #252526;
            border-left: 4px solid #4CAF50;
            border-radius: 3px;
            display: none;
        }
        .error {
            border-left-color: #f44336;
            color: #f44336;
        }
        .state-array {
            color: #9cdcfe;
            font-family: monospace;
        }
        .info {
            font-size: 0.9em;
            color: #a0a0a0;
            margin-top: 10px;
        }
    </style>
</head>
<body>

    <h2>UnHolyPatriarch's Gothic 1 Remake Lockpick Solver</h2>
    
    <div class="controls">
        <label for="numBolts">Number of Bolts:</label>
        <input type="number" id="numBolts" value="5" min="3" max="10">
        
        <button style="margin-left: 20px;" onclick="generateGrid()">Generate Grid</button>
    </div>

    <div id="gridContainer"></div>

    <div class="output-container" id="output"></div>

    <script>
        // System Limits
        const MIN_BOUND = 1;
        const MAX_BOUND = 7;

        window.onload = generateGrid;

        function generateGrid() {
            const numBolts = parseInt(document.getElementById("numBolts").value);
            const container = document.getElementById("gridContainer");
            
            let html = `<table><tr><th></th>`;
            for (let i = 1; i <= numBolts; i++) {
                html += `<th>Bolt ${i} Affected</th>`;
            }
            html += `<th>Starting Position</th></tr>`;

            for (let i = 1; i <= numBolts; i++) {
                let positionLabel = "";
                if (i === 1) positionLabel = `<span class="sub-label">(Furthest Back)</span>`;
                else if (i === numBolts) positionLabel = `<span class="sub-label">(Closest)</span>`;

                html += `<tr><th>Bolt ${i} Actor${positionLabel}</th>`;
                for (let j = 1; j <= numBolts; j++) {
                    if (i === j) {
                        html += `<td>
                                    <select id="mat_${i-1}_${j-1}" disabled class="hard-set">
                                        <option value="1" selected>Match</option>
                                    </select>
                                 </td>`;
                    } else {
                        html += `<td>
                                    <select id="mat_${i-1}_${j-1}">
                                        <option value="1">Match</option>
                                        <option value="0" selected>Nothing</option>
                                        <option value="-1">Reverse</option>
                                    </select>
                                 </td>`;
                    }
                }
                html += `<td><input type="number" id="start_${i-1}" value="1" min="1" max="7"></td></tr>`;
            }
            html += `</table><br><button onclick="solvePuzzle()">Calculate Sequence</button>`;
            
            container.innerHTML = html;
            document.getElementById("output").style.display = "none";
        }

        function solvePuzzle() {
            const numBolts = parseInt(document.getElementById("numBolts").value);
            const targetPos = 4; // Hardcoded target position for Gothic 1 Remake
            const maxStep = 6; // Hardcoded to the mathematical maximum
            const output = document.getElementById("output");
            
            let matrix = [];
            let startState = [];
            let targetDiff = [];

            for (let i = 0; i < numBolts; i++) {
                let startVal = parseFloat(document.getElementById(`start_${i}`).value);
                startState.push(startVal);
                targetDiff.push(targetPos - startVal);
            }

            for (let i = 0; i < numBolts; i++) {
                let row = [];
                for (let j = 0; j < numBolts; j++) {
                    row.push(parseFloat(document.getElementById(`mat_${j}_${i}`).value));
                }
                matrix.push(row);
            }

            let totalMovesRequired = gaussianElimination(matrix, targetDiff);
            
            if (!totalMovesRequired || totalMovesRequired.some(isNaN)) {
                showOutput("Error: No mathematical solution exists for this matrix configuration.", true);
                return;
            }

            let sequence = findBoundedSequence(startState, matrix, totalMovesRequired, maxStep);

            if (sequence.length === 0 && totalMovesRequired.some(m => m !== 0)) {
                showOutput("Error: Found the required moves, but could not find a sequence that prevents the bolts from dropping below 1 or exceeding 7.", true);
                return;
            }

            formatAndDisplayOutput(sequence, startState);
        }

        function gaussianElimination(A, b) {
            let n = A.length;
            let M = [];
            for (let i = 0; i < n; i++) {
                M.push([...A[i], b[i]]);
            }

            for (let i = 0; i < n; i++) {
                let maxEl = Math.abs(M[i][i]);
                let maxRow = i;
                for (let k = i + 1; k < n; k++) {
                    if (Math.abs(M[k][i]) > maxEl) {
                        maxEl = Math.abs(M[k][i]);
                        maxRow = k;
                    }
                }

                let tmp = M[maxRow];
                M[maxRow] = M[i];
                M[i] = tmp;

                if (M[i][i] === 0) return null;
                
                for (let k = i + 1; k < n; k++) {
                    let c = -M[k][i] / M[i][i];
                    for (let j = i; j <= n; j++) {
                        if (i === j) M[k][j] = 0;
                        else M[k][j] += c * M[i][j];
                    }
                }
            }

            let x = new Array(n).fill(0);
            for (let i = n - 1; i >= 0; i--) {
                x[i] = M[i][n] / M[i][i];
                for (let k = i - 1; k >= 0; k--) {
                    M[k][n] -= M[k][i] * x[i];
                }
            }
            
            return x.map(val => Math.round(val));
        }

        function findBoundedSequence(startState, matrix, totalMoves, maxStep) {
            let bestPath = [];
            let minActions = Infinity;
            
            // Failsafe to prevent the browser from freezing on incredibly complex paths
            let iterations = 0;
            const MAX_ITERATIONS = 500000; 

            function dfs(currentState, remainingMoves, path) {
                if (iterations++ > MAX_ITERATIONS) return;

                const actionsSoFar = path.length;
                
                // Prune paths that are already longer than our best found solution
                if (actionsSoFar >= minActions) return; 

                // If target reached, save it and shrink our minimum threshold
                if (remainingMoves.every(r => r === 0)) {
                    bestPath = [...path];
                    minActions = actionsSoFar;
                    return; 
                }

                let options = [];
                for (let i = 0; i < remainingMoves.length; i++) {
                    if (remainingMoves[i] !== 0) options.push(i);
                }
                
                // Sort to explore the largest remaining requirements first
                options.sort((a, b) => Math.abs(remainingMoves[b]) - Math.abs(remainingMoves[a]));

                for (let boltIdx of options) {
                    const dir = Math.sign(remainingMoves[boltIdx]);
                    const maxPossible = Math.min(Math.abs(remainingMoves[boltIdx]), maxStep);

                    for (let stepSize = maxPossible; stepSize >= 1; stepSize--) {
                        let nextState = [...currentState];
                        let isValidMove = true;

                        for (let i = 0; i < nextState.length; i++) {
                            nextState[i] += dir * stepSize * matrix[i][boltIdx];
                            if (nextState[i] < MIN_BOUND || nextState[i] > MAX_BOUND) {
                                isValidMove = false;
                                break;
                            }
                        }

                        if (isValidMove) {
                            let nextRemaining = [...remainingMoves];
                            nextRemaining[boltIdx] -= dir * stepSize;
                            const newPath = [...path, {bolt: boltIdx + 1, dir: dir, count: stepSize, state: nextState}];
                            
                            // Let it continue searching the branch rather than returning early
                            dfs(nextState, nextRemaining, newPath);
                        }
                    }
                }
            }

            if (totalMoves.some(m => m !== 0)) {
                dfs(startState, [...totalMoves], []);
            }
            return bestPath;
        }

        function formatAndDisplayOutput(sequence, startState) {
            if (sequence.length === 0) {
                showOutput("<strong>Lock is already at the target positions!</strong>", false);
                return;
            }

            let html = `<h3>Solution Found (${sequence.length} actions):</h3>`;
            html += `<p><em>Starting State: <span class="state-array">[${startState.join(", ")}]</span></em></p><ol>`;
            
            for (let move of sequence) {
                let direction = move.dir === 1 ? "Left" : "Right";
                html += `<li><strong>Move Bolt ${move.bolt} ${direction}</strong> by <strong>${move.count}</strong> 
                         <br><span class="state-array">New state: [${move.state.join(", ")}]</span></li>`;
            }
            html += `</ol>`;

            showOutput(html, false);
        }

        function showOutput(html, isError) {
            const output = document.getElementById("output");
            output.innerHTML = html;
            output.className = isError ? "output-container error" : "output-container";
            output.style.display = "block";
        }
    </script>
</body>
</html>
