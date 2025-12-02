<script lang="ts">
	import EditorWrapper from '$lib/components/EditorWrapper.svelte';
	import { GalleryHorizontal } from '@lucide/svelte';
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';
	import Pomodorotimer from './pomodorotimer.svelte';
	
    // Define the original array (omitted for brevity, assume your full array is here)
	let questions = [
		// Section 2 - Question 2
		{ 
			id: 'K23 q2.0', 
			title: 'K23: 2. Ariane 5 -kantoraketti',
			material: {
				url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#2.A',
				label: '2.A'
			},
			description: 'Ariane 5 on kantoraketti, jota käytetään satelliittien laukaisemiseen.',
			isk23: true,
			isCompleted: false
		},
		{ 
			id: 'K23 q2.1', 
			title: 'K23: 2.1 Laadi graafinen esitys raketin vauhdista ajan funktiona.',
			description: 'Laadi esitys siten, että siinä näkyvät aineiston pisteet ja että siitä voi lukea raketin vauhdin millä tahansa ajanhetkellä aikavälillä 0 s – 1 500 s.',
			isk23: true,
			isCompleted: false
		},
		{ 
			id: 'K23 q2.2', 
			title: 'K23: 2.2 Kuinka pitkän matkan raketti kulki radallaan aikavälillä 0 s – 1 500 s?',
			isk23: true,
			isCompleted: false
		},
		{ 
			id: 'K23 q2.3', 
			title: 'K23: 2.3 Kuinka suuri oli raketin kiihtyvyys radallaan aikavälillä 700 s – 1 400 s?',
			isk23: true,
			isCompleted: false
		},
        // ... all other questions ...
        { id: 'K23 q5.0', title: 'K23: 5. Kynttilä', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#5.A', label: '5' }, description: '...', isk23: true, isCompleted: false },
		{ id: 'K23 q5.1', title: 'K23: 5.1 Laadi graafinen esitys kynttilän pituudesta ajan funktiona.', description: '...', isk23: true, isCompleted: false },
		{ id: 'K23 q5.2', title: 'K23: 5.2 Toinen samanlainen kynttilä poltetaan täynnä vettä olevassa maljakossa, jossa kynttilä kelluu. Kuinka kauan kynttilä palaa maljakossa?', description: '...', isk23: true, isCompleted: false },
        // ... and so on ...
	];
    
    // NOTE: Replace these placeholder interfaces with actual types if available
	interface Question { id: string; title: string; material?: { url: string; label: string }; description?: string; isk23: boolean; iss22?: boolean; isK24?: boolean; isK25?: boolean; isCompleted: boolean; }
    interface QuestionGroup { mainId: string; mainTitle: string; questions: Question[]; isCompleted: boolean; }

	// STATE VARIABLES
	let currentQuestionGroupIndex = 0; // Index for navigating between main questions (groups)
	let completedCount = 0; // Total number of individual subquestions completed (keep original logic)
    let excludedCmds: string[] = []; // Required for EditorWrapper

    // NEW: Array to hold grouped questions
	let questionGroups: QuestionGroup[] = [];

	// REACTIVE STATE: The currently selected question group
	$: currentQuestionGroup = questionGroups[currentQuestionGroupIndex];

	// --- LOGIC FUNCTIONS ---

    /** Groups the flat 'questions' array into main questions with their subquestions. */
	function groupQuestions() {
        const groupsMap = new Map<string, QuestionGroup>();

        for (const q of questions) {
            // Extracts the main question ID, e.g., 'K23 q5.0' from 'K23 q5.1'
            const parts = q.id.split(' ');
            const qIdWithoutSub = parts[1].split('.')[0]; 
            const mainIdPrefix = parts[0]; 
            const mainId = `${mainIdPrefix} ${qIdWithoutSub}.0`; 

            let group = groupsMap.get(mainId);

            if (!group) {
                // Find the full main question object (the .0 item)
                const mainQuestion = questions.find(item => item.id === mainId);
                
                // Initialize the group structure
                group = {
                    mainId: mainId,
                    mainTitle: mainQuestion?.title || mainId,
                    questions: [],
                    isCompleted: false 
                };
                groupsMap.set(mainId, group);
            }

            group.questions.push(q);
        }
        
        // Convert Map values to a plain Array for indexed access/navigation
        questionGroups = Array.from(groupsMap.values());
    }

    // --- Navigation functions adapted for groups ---
	function previousQuestion() {
		if (currentQuestionGroupIndex > 0) {
			currentQuestionGroupIndex -= 1;
		}
	}

	function nextQuestion() {
		if (currentQuestionGroupIndex < questionGroups.length - 1) {
			currentQuestionGroupIndex += 1;
		}
	}
    
    // --- Other utility functions (stubbed for brevity) ---
    function checkAnswer() { 
        // This logic needs to be fully updated for the new view, 
        // but for now, you can keep the original "open PDF" logic 
        // using the main question (index 0) of the current group.
        
        if (!currentQuestionGroup) return;

        const mainQ = currentQuestionGroup.questions.find(q => q.id === currentQuestionGroup.mainId) || currentQuestionGroup.questions[0];

        if (mainQ) {
             if (mainQ.isk23 == true) {
                 window.open("https://drive.google.com/file/d/17eKbwTU-_cnZQSHAPCZHD81LxaisM_zk/view?pli=1", '_blank')?.focus();
             } else if (mainQ.iss22 == true) {
                 window.open("https://drive.google.com/file/d/12UxfOG6F7nIE2wsc9GG8gDgxF0t-UXdE/view", '_blank')?.focus();
             } 
             // ... and so on for other year checks
        }
    }
    
	function saveCompletedQuestions() { /* ... original logic ... */ }
	function loadCompletedQuestions() { /* ... original logic ... */ }
    // ... all other utility functions like export...

	onMount(() => {
        loadCompletedQuestions();
        groupQuestions();
        completedCount = questions.filter(q => q.isCompleted).length;
	});
</script>

<svelte:head>
    </svelte:head>

{#if currentQuestionGroup}
    <div class="content-menu-top-bar-container">
        <h1 class="main-title">Fysiikan Yo Kone</h1>
        <p class="subtitle">Kysymys {currentQuestionGroupIndex + 1} / {questionGroups.length} (Pääkysymykset)</p>
    </div>

    <div class="progress-container">
        <div class="progress-bar" style="width: {((currentQuestionGroupIndex + 1) / questionGroups.length) * 100}%"></div>
    </div>

    <div class="question-card">
        <div class="question-header">
            <h3 class="question-title"> 
                {currentQuestionGroup.mainTitle} 
                {#if currentQuestionGroup.questions[0].material && currentQuestionGroup.questions[0].material.url}
                    <a href={currentQuestionGroup.questions[0].material.url} target="_blank" rel="noopener noreferrer" class="material-link">
                        📎 Aineisto {currentQuestionGroup.questions[0].material.label}
                    </a>
                {/if}
            </h3>
            {#if currentQuestionGroup.questions[0].description}
                <p class="question-description">{currentQuestionGroup.questions[0].description}</p>
            {/if}
        </div>

        {#each currentQuestionGroup.questions as question (question.id)}
            <div class="subquestion-block">
                <h4 class="subquestion-title">
                    {question.title}
                </h4>
                
                {#if question.id !== currentQuestionGroup.mainId && question.description}
                    <p class="subquestion-description">{question.description}</p>
                {/if}

                <div class="editor-container">
                    <EditorWrapper 
                        editorId={question.id} 
                        excludedCommands={excludedCmds} 
                        imagexasizewidth={500} 
                        imagemaxsizeheight={350} 
                    />
                </div>
            </div>
        {/each}

        <div class="button-row">
            <button id="checkButton" on:click={checkAnswer}>Katso vastaus</button>
            <span class="completion-status"> {completedCount}/{questions.length} Tehty </span>
        </div>
    </div>

    <div class="navigation">
        <button class="nav-button" on:click={previousQuestion} disabled={currentQuestionGroupIndex === 0} > 
            ← Edellinen 
        </button>

        <div class="question-selector">
            <select bind:value={currentQuestionGroupIndex} class="question-dropdown">
                {#each questionGroups as group, index}
                    <option value={index}> 
                        {group.mainId.toUpperCase().split(' ')[1]} - {group.mainTitle}
                    </option>
                {/each}
            </select>
        </div>

        <button class="nav-button" on:click={nextQuestion} disabled={currentQuestionGroupIndex === questionGroups.length - 1} > 
            Seuraava → 
        </button>
    </div>
{/if}


<style>


:global(body) {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
		background-color: #f5f5f5;
		margin: 0;
		padding: 0;
	}



	h1 {
		text-align: center;
		margin-bottom: 10px;
	}

	.subtitle {
		text-align: center;
		color: #666;
		margin-bottom: 20px;
	}

	.progress-container {
		width: 100%;
		height: 6px;
		background-color: #e0e0e0;
		border-radius: 3px;
		margin-bottom: 30px;
		overflow: hidden;
	}

	.progress-bar {
		height: 100%;
		background: linear-gradient(90deg, #4CAF50, #45a049);
		transition: width 0.3s ease;
	}

	.question-card {
		background: white;
		border-radius: 8px;
		padding: 30px;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
		margin-bottom: 20px;
		min-height: 400px;
	}

	.question-header {
		margin-bottom: 20px;
	}

	.question-title {
		margin-top: 0;
		margin-bottom: 10px;
		color: #333;
		font-size: 1.1rem;
		line-height: 1.6;
		display: flex;
		align-items: center;
		flex-wrap: wrap;
		gap: 10px;
	}

	.question-description {
		color: #666;
		font-size: 0.95rem;
		margin: 0;
		line-height: 1.5;
	}

	.material-link {
		color: #1976d2;
		text-decoration: none;
		font-weight: 500;
		padding: 4px 12px;
		background-color: #e3f2fd;
		border-radius: 4px;
		font-size: 0.9rem;
		transition: all 0.2s ease;
		white-space: nowrap;
	}

	.material-link:hover {
		background-color: #bbdefb;
		color: #1565c0;
		transform: translateY(-1px);
	}

	.editor-container {
		width: auto;
		height: auto;
		border: 1px solid #ddd;
		border-radius: 4px;
	}

	.navigation {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 20px;
		margin-bottom: 30px;
	}

	.nav-button {
		padding: 12px 24px;
		font-size: 16px;
		font-weight: 500;
		background-color: #4CAF50;
		color: white;
		border: none;
		border-radius: 4px;
		cursor: pointer;
		transition: all 0.2s ease;
		min-width: 120px;
	}

	.nav-button:hover:not(:disabled) {
		background-color: #45a049;
		transform: translateY(-1px);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
	}

	.nav-button:disabled {
		background-color: #cccccc;
		cursor: not-allowed;
		opacity: 0.6;
	}

	.question-selector {
		flex: 1;
		max-width: 400px;
	}

	.question-dropdown {
		width: 100%;
		padding: 10px 15px;
		font-size: 14px;
		border: 2px solid #ddd;
		border-radius: 4px;
		background-color: white;
		cursor: pointer;
		transition: border-color 0.2s ease;
	}

	.question-dropdown:hover {
		border-color: #4CAF50;
	}

	.question-dropdown:focus {
		outline: none;
		border-color: #4CAF50;
		box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.1);
	}



	/* Responsive design */
	

	#checkButton {

	 text-align: center;
	 border-radius: 8px;
	 color: #f1f8f4;
	 background-color: #4CAF50;
	 padding: 8px;
	font-weight: 600;
	}

	#checkButton:hover {
		border: 1px solid white;
		text-align: center;
		border-radius: 8px;
		color: #f1f8f4;
		background-color: #09eb11;
		padding: 8px;
	}

	.button-row {
		display: flex;
		gap: 8px;
		align-items: center;
		margin-top: 8px;
		flex-wrap: wrap;
	}


	.completion-status {
		display: flex;
		align-items: center;
		font-weight: 600;
		color: #4CAF50;
		font-size: 0.95rem;
		margin-left: auto;
		padding: 8px 16px;
		background-color: #f1f8f4;
		border-radius: 4px;
		border: 1px solid #4CAF50;
	}
/* 

	.content-menu-top-bar-container {
		background-color: #e1e7e2;
		padding: 10px;
		display: flex;
		flex-direction: row;
		align-content: center;
		justify-content: center;
		gap: 10px;
	}


	.content-menu-top-bar-container-button-1 {
		color: #413f3f;
		background-color: #4CAF50;
		color: white;
		border-radius: 5px;
      padding-bottom: 2.5px;
		padding-top: 2.5px;
		padding-left: 5px;
		padding-right: 5px;

	}

	.content-menu-top-bar-container-button {
		color: #413f3f;
		background-color: #4CAF50;
		color: white;
		border-radius: 5px;
		padding: 5px;
	} */







    /* Add basic styling for the new subquestion layout to make it readable */
    .subquestion-block {
        margin-top: 25px;
        padding: 15px;
        border-left: 5px solid #4CAF50; /* A visual separator */
        background-color: #f7f7f7;
        border-radius: 8px;
    }
    
    .subquestion-title {
        margin-top: 0;
        margin-bottom: 15px;
        font-size: 1.15rem;
        font-weight: 600;
        color: #333;
    }
    
    .subquestion-description {
        margin-bottom: 10px;
        font-style: italic;
        color: #555;
    }

    /* ... Keep the rest of your original CSS ... */

    /* Ensure original styles for navigation and buttons are here for full functionality */
</style>