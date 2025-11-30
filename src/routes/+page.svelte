<script lang="ts">
	import EditorWrapper from '$lib/components/EditorWrapper.svelte';

	const questions = [
		// Section 2 - Question 2
		{ 
			id: 'K23 q2.0', 
			title: 'K23: 2. Ariane 5 -kantoraketti',
			material: {
				url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#2.A',
				label: '2.A'
			},
			description: 'Ariane 5 on kantoraketti, jota käytetään satelliittien laukaisemiseen.'
		},
		{ 
			id: 'K23 q2.1', 
			title: 'K23: 2.1 Laadi graafinen esitys raketin vauhdista ajan funktiona.',
			description: 'Laadi esitys siten, että siinä näkyvät aineiston pisteet ja että siitä voi lukea raketin vauhdin millä tahansa ajanhetkellä aikavälillä 0 s – 1 500 s.'
		},
		{ 
			id: 'K23 q2.2', 
			title: 'K23: 2.2 Kuinka pitkän matkan raketti kulki radallaan aikavälillä 0 s – 1 500 s?'
		},
		{ 
			id: 'K23 q2.3', 
			title: 'K23: 2.3 Kuinka suuri oli raketin kiihtyvyys radallaan aikavälillä 700 s – 1 400 s?'
		},

		// Section 2 - Question 3

		//question 3 is

		// { 
		// 	id: 'q3.0', 
		// 	title: '3. Lämmönsiirtokoneet',
		// 	material: { },
		// 	description: 'Valitse lämmönsiirtokoneisiin liittyvissä osatehtävissä 3.1–3.8 vastaus, joka kuvaa tilannetta parhaiten fysikaalisesti.'
		// },
		// { id: 'q3.1', title: '3.1 Miksi energian siirtyminen kylmästä ulkoilmasta lämpöä siirtävään aineeseen on mahdollista ulkoyksikössä?', description: '' },
		// { id: 'q3.2', title: '3.2 Mitä lämpöä siirtävälle aineelle tapahtuu, kun se on höyrystimessä?', description: '' },
		// { id: 'q3.3', title: '3.3 Lämpöpumpun sähköteho on 1 000 W. Oikea suuruusluokka lämpöpumpun lämmitysteholle on...', description: '' },
		// { id: 'q3.4', title: '3.4 Mitä tapahtuu jääkaapin sähkönkulutukselle, jos huoneen lämpötila pysyvästi nousee?', description: '' },
		// { id: 'q3.5', title: '3.5 Käynnissä olevan jääkaapin ovi unohdetaan auki pitkäksi aikaa. Mitä huoneen lämpötilalle tapahtuu?', description: '' },
		// { id: 'q3.6', title: '3.6 Mikä seuraavista kaavioista esittää lämmönsiirtokoneen toimintaperiaatetta?', description: '' },
		// { id: 'q3.7', title: '3.7 Mikä seuraavista graafeista esittää ideaalisen lämmönsiirtokoneen toimintaa? Aine on tässä tilanteessa koko ajan kaasua.', description: '' },
		// { id: 'q3.8', title: '3.8 Eräässä ideaalisen lämmönsiirtokoneen työvaiheessa aineeseen tehdään työtä, mutta sen ja ympäristön välillä ei siirry lämpöä. Mitä kaasun lämpötilalle ja tilavuudelle tapahtuu?', description: '' },

		// Section 2 - Question 4
		{ id: 'K23 q4.0', title: 'K23: 4. Kondensaattori', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#4.A', label: '4' }, description: 'Aineisto: 4.A Kondensaattorin varautumis- ja purkautumiskäyrä, 4.B Täydennettävä piiri, 4.C Kytkin, 4.D Vastus, 4.E Jännitemittari. Kondensaattoria ensin varataan ja sen jälkeen kondensaattorin varausta puretaan.' },
		{ id: 'K23 q4.1', title: 'K23: 4.1 Täydennä kuvan 4.B keskeneräinen kytkentäkaavio siten, että piirillä voisi tuottaa kuvan 4.A mukaisen kuvaajan. Käytä kahta kytkintä, johtimia, vastusta sekä jännitemittaria.', description: '' },
		{ id: 'K23 q4.2', title: 'K23: 4.2 Onko virran suunta kuvan 4.B pisteessä P ylös- vai alaspäin varautumiskäyrän ajanhetkillä t₁ ja t₂?', description: '' },
		{ id: 'K23 q4.3', title: 'K23: 4.3 Miten muuttaisit piirin komponentteja, jos haluat hidastaa kondensaattorin varautumista ja purkautumista?', description: '' },

		// Section 2 - Question 5
		{ id: 'K23 q5.0', title: 'K23: 5. Kynttilä', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#5.A', label: '5' }, description: 'Aineisto: 5.A Mittausaineisto: Kynttilän pituus ajan funktiona, 5.B Valokuva maljakossa kelluvasta kynttilästä, 5.C Kynttilän voimakuvio. Kynttilää poltetaan ja sen pituus mitataan palamisajan funktiona. Kynttilän pituus alussa on 189 mm, halkaisija on 21 mm ja keskimääräinen tiheys on 862 kg/m³.' },
		{ id: 'K23 q5.1', title: 'K23: 5.1 Laadi graafinen esitys kynttilän pituudesta ajan funktiona. Esitä graafissa aineiston pisteet ja mittausaineistoon sopiva malli.', description: '' },
		{ id: 'K23 q5.2', title: 'K23: 5.2 Toinen samanlainen kynttilä poltetaan täynnä vettä olevassa maljakossa, jossa kynttilä kelluu. Jotta kynttilä pysyisi pystyssä, sen tyveen kiinnitetään painoksi metallirengas, jonka massa on 3,5 g. Kuinka kauan kynttilä palaa maljakossa?', description: '' },

		// Section 2 - Question 6
		{ id: 'K23 q6.0', title: 'K23: 6. Sipsipussin rapistelu', material: { }, description: 'Yhdysvaltalainen yritys toi vuonna 2010 markkinoille biohajoavan Sun Chips -perunalastupussin. Pussin ongelmana oli voimakas rapisteluääni, jonka intensiteettitaso ylsi peräti 95 desibeliin. Oletetaan, että intensiteettitaso mitattiin 1,0 metrin etäisyydeltä.' },
		{ id: 'K23 q6.1', title: 'K23: 6.1 Mikä on intensiteettitaso, kun viisi ihmistä rapistelee kukin omaa sipsipussiaan samanaikaisesti 1,0 metrin etäisyydellä mittarista?', description: '' },
		{ id: 'K23 q6.2', title: 'K23: 6.2 Tuotekehityksellä rapisteluäänen intensiteettitaso saatiin laskettua 75 desibeliin. Kuinka monta prosenttia äänen intensiteetti oli tällöin alkuperäisestä intensiteetistä?', description: '' },
		{ id: 'K23 q6.3', title: 'K23: 6.3 Arvioi, millä etäisyydellä alkuperäisen sipsipussin intensiteettitaso (95 dB) vastaa tuulen huminaa, jonka intensiteettitaso on 30 dB.', description: '' },
		{ id: 'K23 q6.4', title: 'K23: 6.4 Miksi osatehtävässä 6.3 laskettu etäisyyden arvio ei ole realistinen käytännön tilanteessa?', description: '' },

		// Section 2 - Question 7
		{ id: 'K23 q7.0', title: 'K23: 7. Käsikäyttöinen generaattori', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#7.A', label: '7' }, description: 'Aineisto: 7.A Kuva: Käsikäyttöinen generaattori, 7.B Simulaatio generaattorin tuottamasta jännitteestä. Kun kestomagneetin sisällä oleva käämi pyörii tasaisella kulmanopeudella, syntyy johtimien välille jaksollisesti vaihteleva jännite.' },
		{ id: 'K23 q7.1', title: 'K23: 7.1 Selitä, miten jännite syntyy.', description: '' },
		{ id: 'K23 q7.2', title: 'K23: 7.2 Johda induktiolaista lähtien lauseke |e|=NBAω käämiin indusoituvan jännitteen huippuarvolle. Lausekkeessa N on käämin kierroslukumäärä, B kestomagneetin magneettivuon tiheys, A käämin pinta-ala ja ω käämin kulmanopeus.', description: '' },
		{ id: 'K23 q7.3', title: 'K23: 7.3 Simulaatio generaattorin tuottamasta jännitteestä on aineistossa 7.B. Neliön muotoisessa käämissä on 150 kierrosta ja käämin sivun pituus on 6 cm. Määritä simulaation avulla magneettivuon tiheys käämin kohdalla.', description: '' },

		// Section 2 - Question 8
		{ id: 'K23 q8.0', title: 'K23: 8. Pieni Curie', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#8.A', label: '8' }, description: 'Aineisto: 8.A Artikkeli: "Marie Curie laboratoriossa ja rintamalla", 8.B Valokuva fluoroskopiakuvantamisesta ensimmäisen maailmansodan ajalta, 8.C Röntgenkuva influenssapotilaan keuhkoista vuodelta 1918. Artikkeli kuvaa ensimmäisessä maailmansodassa käytettyjä siirrettäviä röntgenkuvauslaitteita.' },
		{ id: 'K23 q8.1', title: 'K23: 8.1 Miksi röntgenlaitteita ei tuolloin voitu useinkaan kytkeä suoraan sähköverkkoon?', description: '' },
		{ id: 'K23 q8.2', title: 'K23: 8.2 Säteily voitiin havaita kuvalevyllä tai fluoroskoopilla. Kumpaa tapaa käyttäisit itse nykypäivänä ja miksi?', description: '' },
		{ id: 'K23 q8.3', title: 'K23: 8.3 Miksi aineistossa 8.A kuvattuja vammoja tai keuhkosairauksia voidaan havaita röntgenkuvantamisella?', description: '' },

		// Section 3 - Question 9
		{ id: 'K23 q9.0', title: 'K23: 9. Gammasäteilyn ja aineen välinen vuorovaikutus', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#9.A', label: '9' }, description: 'Aineisto: 9.A Todennäköisin fotonin vuorovaikutustapa eri energioilla ja alkuaineen järjestysluvuilla, 9.B Kahden eri ilmaisimen tuottamat energiaspektrit 662 keV:n gammalähteelle. Gammafotoni eli korkeaenergiainen fotoni vuorovaikuttaa aineen kanssa kolmella eri tavalla.' },
		{ id: 'K23 q9.1', title: 'K23: 9.1 Mitä fotonille tapahtuu, ja mihin sen energia siirtyy valosähköilmiössä ja parinmuodostuksessa?', description: '' },
		{ id: 'K23 q9.2', title: 'K23: 9.2 Comptonin ilmiössä fotoni siroaa elektronista. Mikä on suurin liike-energia, jonka elektroni voi saada fotonilta, kun 662 keV:n fotoni siroaa siitä?', description: '' },
		{ id: 'K23 q9.3', title: 'K23: 9.3 Kahdella erilaisella tilavuudeltaan pienellä ilmaisimella havaittiin Cs-137-säteilylähteen tuottamaa 662 keV:n gammasäteilyä. Selitä, mitä on todennäköisimmin tapahtunut ilmaisimissa, kun spektreihin on ilmaantunut tapahtumia alle 400 keV:n alueelle. Kumpi kuvan 9.B spektreistä (A/B) on muovista valmistetun ilmaisimen spektri?', description: '' },

		// Section 3 - Question 10
		{ id: 'K23 q10.0', title: 'K23: 10. Parafiinin sulamislämpö', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#10.A', label: '10' }, description: 'Aineisto: 10.A Piirrospohja. Haluat kokeellisesti määrittää materiaalin ominaissulamislämmön fysiikan oppitunnilla. Olet valinnut materiaaliksi parafiinin, jonka sulamispiste on 60 °C. Käytettävissä: solupolystyreeniastia, vettä ja vedenkeitin, kiinteätä parafiinia 20 °C:ssa, sekä fysiikan luokan mittausvälineet.' },
		{ id: 'K23 q10.1', title: 'K23: 10.1 Mitkä ovat työn päävaiheet ja niissä tehtävät mittaukset? Miten määrität mittaustuloksista parafiinin ominaissulamislämmön? Esitä tarvittavat suureyhtälöt. Mitkä numeroidun listan välineistä tarvitset?', description: '' },
		{ id: 'K23 q10.2', title: 'K23: 10.2 Vertaat lopuksi mittauksista saamaasi sulamislämmön arvoa kirjallisuusarvoon. Luettele kolme tärkeätä tekijää, jotka aiheuttavat mittaamaasi arvoon poikkeaman kirjallisuusarvosta.', description: '' },

		// Section 3 - Question 11
		{ id: 'K23 q11.0', title: 'K23: 11. James Webb -avaruusteleskooppi', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#11.A', label: '11' }, description: 'Aineisto: 11.A James Webb -avaruusteleskooppi, 11.B Aurinko-Maa-järjestelmän Lagrangen piste L2. Joulupäivänä 2021 laukaistiin James Webb -avaruusteleskooppi Lagrangen pisteeseen L2. Teleskooppi kiertää Aurinkoa pysyen Auringon ja Maan kautta kulkevalla suoralla. Teleskooppi toimii lähinnä infrapuna-alueella.' },
		{ id: 'K23 q11.1', title: 'K23: 11.1 Miksi alhainen lämpötila on olennainen tekijä infrapunasäteilyn havainnoinnissa?', description: '' },
		{ id: 'K23 q11.2', title: 'K23: 11.2 Miksi kuvassa 11.A näkyvä teleskoopin lämpösuoja ei ole yhtenäinen kerros, vaan koostuu viidestä erillään olevasta kerroksesta?', description: '' },
		{ id: 'K23 q11.3', title: 'K23: 11.3 Piirrä teleskoopin voimakuvio ja nimeä voimat.', description: '' },
		{ id: 'K23 q11.4', title: 'K23: 11.4 Teleskoopin etäisyys Maasta on 1,5 miljoonaa kilometriä. Perustele tämä osoittamalla, että Newtonin II laki toteutuu kyseisellä etäisyyden arvolla.', description: '' },
	];

	let currentQuestionIndex = 0;
	$: currentQuestion = questions[currentQuestionIndex];
	
	function nextQuestion() {
		if (currentQuestionIndex < questions.length - 1) {
			currentQuestionIndex++;
		}
	}
	
	function previousQuestion() {
		if (currentQuestionIndex > 0) {
			currentQuestionIndex--;
		}
	}
	
	function goToQuestion(index: number) {
		currentQuestionIndex = index;
	}

	const excludedCmds = [
		'searchAndReplace', 'bulletList', 'alignLeft', 'alignRight', 
		'audio-placeholder', 'taskList', 'orderedList', 'alignJustify', 
		'video-placeholder', 'iframe-placeholder', 'underline', 'subscript', 
		'heading1', 'heading2', 'bold', 'alignCenter', 'font increment', 'undo', 'redo', 'italic'
	];
</script>

<div class="container">
	<h1>Fysiikan Yo Kone</h1>
	<p class="subtitle">Question {currentQuestionIndex + 1} of {questions.length}</p>

	<!-- Progress bar -->
	<div class="progress-container">
		<div class="progress-bar" style="width: {((currentQuestionIndex + 1) / questions.length) * 100}%"></div>
	</div>

	<!-- Question card -->
	<div class="question-card">
		<div class="question-header">
			<h3 class="question-title">
				{currentQuestion.title}
				{#if currentQuestion.material && currentQuestion.material.url}
					<a href={currentQuestion.material.url} target="_blank" rel="noopener noreferrer" class="material-link">
						📎 Aineisto {currentQuestion.material.label}
					</a>
				{/if}
			</h3>
			{#if currentQuestion.description}
				<p class="question-description">{currentQuestion.description}</p>
			{/if}
		</div>
		
		<div class="editor-container">
			{#key currentQuestion.id}
				<EditorWrapper 
					editorId={currentQuestion.id}
					excludedCommands={excludedCmds} 
					imagexasizewidth={500} 
					imagemaxsizeheight={350} 
				/>
			{/key}
		</div>
	</div>

	<!-- Navigation buttons -->
	<div class="navigation">
		<button 
			class="nav-button" 
			on:click={previousQuestion} 
			disabled={currentQuestionIndex === 0}
		>
			← Previous
		</button>
		
		<div class="question-selector">
			<select bind:value={currentQuestionIndex} class="question-dropdown">
				{#each questions as question, index}
					<option value={index}>
						{question.id.toUpperCase()} - {question.title.split('.')[0]}.{question.title.split('.')[1]?.split(' ')[0] || ''}
					</option>
				{/each}
			</select>
		</div>
		
		<button 
			class="nav-button" 
			on:click={nextQuestion} 
			disabled={currentQuestionIndex === questions.length - 1}
		>
			Next →
		</button>
	</div>

	<!-- Question grid for quick navigation -->
	<div class="question-grid">
		{#each questions as question, index}
			<button 
				class="question-number" 
				class:active={index === currentQuestionIndex}
				on:click={() => goToQuestion(index)}
				title={question.title}
			>
				{question.id.replace('q', '')}
			</button>
		{/each}
	</div>
</div>

<style>
	:global(body) {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
		background-color: #f5f5f5;
		margin: 0;
		padding: 0;
	}

	.container {
		max-width: 1000px;
		margin: 0 auto;
		padding: 20px;
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

	.question-grid {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
		gap: 8px;
		padding: 20px;
		background: white;
		border-radius: 8px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
	}

	.question-number {
		padding: 10px;
		border: 2px solid #e0e0e0;
		border-radius: 4px;
		background: white;
		cursor: pointer;
		font-size: 13px;
		font-weight: 500;
		transition: all 0.2s ease;
	}

	.question-number:hover {
		border-color: #4CAF50;
		background-color: #f1f8f4;
	}

	.question-number.active {
		background-color: #4CAF50;
		color: white;
		border-color: #4CAF50;
	}

	/* Responsive design */
	@media (max-width: 768px) {
		.container {
			padding: 10px;
		}

		.question-card {
			padding: 20px;
		}

		.navigation {
			flex-direction: column;
		}

		.question-selector {
			max-width: 100%;
			width: 100%;
		}

		.nav-button {
			width: 100%;
		}

		.question-grid {
			grid-template-columns: repeat(auto-fill, minmax(50px, 1fr));
		}

		.question-title {
			font-size: 1rem;
		}
	}
</style>