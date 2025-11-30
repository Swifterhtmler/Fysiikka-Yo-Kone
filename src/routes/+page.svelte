<script lang="ts">
	import EditorWrapper from '$lib/components/EditorWrapper.svelte';

	
	// const questions = [
	// 	{ id: 'q2.1', title: '2.1 Esitä vuorokaudessa virranneen veden tilavuus vuoden alusta lasketun päivän numeron funktiona.' },
	// 	{ id: 'q2.2', title: '2.2 Minkä kuukauden aikana vettä virtasi eniten, ja mikä oli sinä kuukautena virranneen veden kokonaistilavuus?' },
	// 	{ id: 'q2.3', title: '2.3 Pirttikosken voimalaitoksessa vesi putoaa 26 metriä. Kuinka paljon energiaa voimalaitos olisi enintään voinut tuottaa 13.3.2022...' }
	// ];


	const questions = [
	// Section 2 - Question 2
	{ id: 'q2.0', title: '2. Ariane 5 -kantoraketti - Aineisto 2.A: Mittausaineisto: Raketin vauhti radallaan ajan funktiona. Ariane 5 on kantoraketti, jota käytetään satelliittien laukaisemiseen.' },
	{ id: 'q2.1', title: '2.1 Laadi graafinen esitys raketin vauhdista ajan funktiona. Laadi esitys siten, että siinä näkyvät aineiston pisteet ja että siitä voi lukea raketin vauhdin millä tahansa ajanhetkellä aikavälillä 0 s – 1 500 s.' },
	{ id: 'q2.2', title: '2.2 Kuinka pitkän matkan raketti kulki radallaan aikavälillä 0 s – 1 500 s?' },
	{ id: 'q2.3', title: '2.3 Kuinka suuri oli raketin kiihtyvyys radallaan aikavälillä 700 s – 1 400 s?' },

	// Section 2 - Question 3
	{ id: 'q3.0', title: '3. Lämmönsiirtokoneet - Valitse lämmönsiirtokoneisiin liittyvissä osatehtävissä 3.1–3.8 vastaus, joka kuvaa tilannetta parhaiten fysikaalisesti.' },
	{ id: 'q3.1', title: '3.1 Miksi energian siirtyminen kylmästä ulkoilmasta lämpöä siirtävään aineeseen on mahdollista ulkoyksikössä?' },
	{ id: 'q3.2', title: '3.2 Mitä lämpöä siirtävälle aineelle tapahtuu, kun se on höyrystimessä?' },
	{ id: 'q3.3', title: '3.3 Lämpöpumpun sähköteho on 1 000 W. Oikea suuruusluokka lämpöpumpun lämmitysteholle on...' },
	{ id: 'q3.4', title: '3.4 Mitä tapahtuu jääkaapin sähkönkulutukselle, jos huoneen lämpötila pysyvästi nousee?' },
	{ id: 'q3.5', title: '3.5 Käynnissä olevan jääkaapin ovi unohdetaan auki pitkäksi aikaa. Mitä huoneen lämpötilalle tapahtuu?' },
	{ id: 'q3.6', title: '3.6 Mikä seuraavista kaavioista esittää lämmönsiirtokoneen toimintaperiaatetta?' },
	{ id: 'q3.7', title: '3.7 Mikä seuraavista graafeista esittää ideaalisen lämmönsiirtokoneen toimintaa? Aine on tässä tilanteessa koko ajan kaasua.' },
	{ id: 'q3.8', title: '3.8 Eräässä ideaalisen lämmönsiirtokoneen työvaiheessa aineeseen tehdään työtä, mutta sen ja ympäristön välillä ei siirry lämpöä. Mitä kaasun lämpötilalle ja tilavuudelle tapahtuu?' },

	// Section 2 - Question 4
	{ id: 'q4.0', title: '4. Kondensaattori - Aineisto: 4.A Kondensaattorin varautumis- ja purkautumiskäyrä, 4.B Täydennettävä piiri, 4.C Kytkin, 4.D Vastus, 4.E Jännitemittari. Kondensaattoria ensin varataan ja sen jälkeen kondensaattorin varausta puretaan.' },
	{ id: 'q4.1', title: '4.1 Täydennä kuvan 4.B keskeneräinen kytkentäkaavio siten, että piirillä voisi tuottaa kuvan 4.A mukaisen kuvaajan. Käytä kahta kytkintä, johtimia, vastusta sekä jännitemittaria.' },
	{ id: 'q4.2', title: '4.2 Onko virran suunta kuvan 4.B pisteessä P ylös- vai alaspäin varautumiskäyrän ajanhetkillä t₁ ja t₂?' },
	{ id: 'q4.3', title: '4.3 Miten muuttaisit piirin komponentteja, jos haluat hidastaa kondensaattorin varautumista ja purkautumista?' },

	// Section 2 - Question 5
	{ id: 'q5.0', title: '5. Kynttilä - Aineisto: 5.A Mittausaineisto: Kynttilän pituus ajan funktiona, 5.B Valokuva maljakossa kelluvasta kynttilästä, 5.C Kynttilän voimakuvio. Kynttilää poltetaan ja sen pituus mitataan palamisajan funktiona. Kynttilän pituus alussa on 189 mm, halkaisija on 21 mm ja keskimääräinen tiheys on 862 kg/m³.' },
	{ id: 'q5.1', title: '5.1 Laadi graafinen esitys kynttilän pituudesta ajan funktiona. Esitä graafissa aineiston pisteet ja mittausaineistoon sopiva malli.' },
	{ id: 'q5.2', title: '5.2 Toinen samanlainen kynttilä poltetaan täynnä vettä olevassa maljakossa, jossa kynttilä kelluu. Jotta kynttilä pysyisi pystyssä, sen tyveen kiinnitetään painoksi metallirengas, jonka massa on 3,5 g. Kuinka kauan kynttilä palaa maljakossa?' },

	// Section 2 - Question 6
	{ id: 'q6.0', title: '6. Sipsipussin rapistelu - Yhdysvaltalainen yritys toi vuonna 2010 markkinoille biohajoavan Sun Chips -perunalastupussin. Pussin ongelmana oli voimakas rapisteluääni, jonka intensiteettitaso ylsi peräti 95 desibeliin. Oletetaan, että intensiteettitaso mitattiin 1,0 metrin etäisyydeltä.' },
	{ id: 'q6.1', title: '6.1 Mikä on intensiteettitaso, kun viisi ihmistä rapistelee kukin omaa sipsipussiaan samanaikaisesti 1,0 metrin etäisyydellä mittarista?' },
	{ id: 'q6.2', title: '6.2 Tuotekehityksellä rapisteluäänen intensiteettitaso saatiin laskettua 75 desibeliin. Kuinka monta prosenttia äänen intensiteetti oli tällöin alkuperäisestä intensiteetistä?' },
	{ id: 'q6.3', title: '6.3 Arvioi, millä etäisyydellä alkuperäisen sipsipussin intensiteettitaso (95 dB) vastaa tuulen huminaa, jonka intensiteettitaso on 30 dB.' },
	{ id: 'q6.4', title: '6.4 Miksi osatehtävässä 6.3 laskettu etäisyyden arvio ei ole realistinen käytännön tilanteessa?' },

	// Section 2 - Question 7
	{ id: 'q7.0', title: '7. Käsikäyttöinen generaattori - Aineisto: 7.A Kuva: Käsikäyttöinen generaattori, 7.B Simulaatio generaattorin tuottamasta jännitteestä. Kun kestomagneetin sisällä oleva käämi pyörii tasaisella kulmanopeudella, syntyy johtimien välille jaksollisesti vaihteleva jännite.' },
	{ id: 'q7.1', title: '7.1 Selitä, miten jännite syntyy.' },
	{ id: 'q7.2', title: '7.2 Johda induktiolaista lähtien lauseke |e|=NBAω käämiin indusoituvan jännitteen huippuarvolle. Lausekkeessa N on käämin kierroslukumäärä, B kestomagneetin magneettivuon tiheys, A käämin pinta-ala ja ω käämin kulmanopeus.' },
	{ id: 'q7.3', title: '7.3 Simulaatio generaattorin tuottamasta jännitteestä on aineistossa 7.B. Neliön muotoisessa käämissä on 150 kierrosta ja käämin sivun pituus on 6 cm. Määritä simulaation avulla magneettivuon tiheys käämin kohdalla.' },

	// Section 2 - Question 8
	{ id: 'q8.0', title: '8. Pieni Curie - Aineisto: 8.A Artikkeli: "Marie Curie laboratoriossa ja rintamalla", 8.B Valokuva fluoroskopiakuvantamisesta ensimmäisen maailmansodan ajalta, 8.C Röntgenkuva influenssapotilaan keuhkoista vuodelta 1918. Artikkeli kuvaa ensimmäisessä maailmansodassa käytettyjä siirrettäviä röntgenkuvauslaitteita.' },
	{ id: 'q8.1', title: '8.1 Miksi röntgenlaitteita ei tuolloin voitu useinkaan kytkeä suoraan sähköverkkoon?' },
	{ id: 'q8.2', title: '8.2 Säteily voitiin havaita kuvalevyllä tai fluoroskoopilla. Kumpaa tapaa käyttäisit itse nykypäivänä ja miksi?' },
	{ id: 'q8.3', title: '8.3 Miksi aineistossa 8.A kuvattuja vammoja tai keuhkosairauksia voidaan havaita röntgenkuvantamisella?' },

	// Section 3 - Question 9
	{ id: 'q9.0', title: '9. Gammasäteilyn ja aineen välinen vuorovaikutus - Aineisto: 9.A Todennäköisin fotonin vuorovaikutustapa eri energioilla ja alkuaineen järjestysluvuilla, 9.B Kahden eri ilmaisimen tuottamat energiaspektrit 662 keV:n gammalähteelle. Gammafotoni eli korkeaenergiainen fotoni vuorovaikuttaa aineen kanssa kolmella eri tavalla.' },
	{ id: 'q9.1', title: '9.1 Mitä fotonille tapahtuu, ja mihin sen energia siirtyy valosähköilmiössä ja parinmuodostuksessa?' },
	{ id: 'q9.2', title: '9.2 Comptonin ilmiössä fotoni siroaa elektronista. Mikä on suurin liike-energia, jonka elektroni voi saada fotonilta, kun 662 keV:n fotoni siroaa siitä?' },
	{ id: 'q9.3', title: '9.3 Kahdella erilaisella tilavuudeltaan pienellä ilmaisimella havaittiin Cs-137-säteilylähteen tuottamaa 662 keV:n gammasäteilyä. Selitä, mitä on todennäköisimmin tapahtunut ilmaisimissa, kun spektreihin on ilmaantunut tapahtumia alle 400 keV:n alueelle. Kumpi kuvan 9.B spektreistä (A/B) on muovista valmistetun ilmaisimen spektri?' },

	// Section 3 - Question 10
	{ id: 'q10.0', title: '10. Parafiinin sulamislämpö - Aineisto: 10.A Piirrospohja. Haluat kokeellisesti määrittää materiaalin ominaissulamislämmön fysiikan oppitunnilla. Olet valinnut materiaaliksi parafiinin, jonka sulamispiste on 60 °C. Käytettävissä: solupolystyreeniastia, vettä ja vedenkeitin, kiinteätä parafiinia 20 °C:ssa, sekä fysiikan luokan mittausvälineet.' },
	{ id: 'q10.1', title: '10.1 Mitkä ovat työn päävaiheet ja niissä tehtävät mittaukset? Miten määrität mittaustuloksista parafiinin ominaissulamislämmön? Esitä tarvittavat suureyhtälöt. Mitkä numeroidun listan välineistä tarvitset?' },
	{ id: 'q10.2', title: '10.2 Vertaat lopuksi mittauksista saamaasi sulamislämmön arvoa kirjallisuusarvoon. Luettele kolme tärkeätä tekijää, jotka aiheuttavat mittaamaasi arvoon poikkeaman kirjallisuusarvosta.' },

	// Section 3 - Question 11
	{ id: 'q11.0', title: '11. James Webb -avaruusteleskooppi - Aineisto: 11.A James Webb -avaruusteleskooppi, 11.B Aurinko-Maa-järjestelmän Lagrangen piste L2. Joulupäivänä 2021 laukaistiin James Webb -avaruusteleskooppi Lagrangen pisteeseen L2. Teleskooppi kiertää Aurinkoa pysyen Auringon ja Maan kautta kulkevalla suoralla. Teleskooppi toimii lähinnä infrapuna-alueella.' },
	{ id: 'q11.1', title: '11.1 Miksi alhainen lämpötila on olennainen tekijä infrapunasäteilyn havainnoinnissa?' },
	{ id: 'q11.2', title: '11.2 Miksi kuvassa 11.A näkyvä teleskoopin lämpösuoja ei ole yhtenäinen kerros, vaan koostuu viidestä erillään olevasta kerroksesta?' },
	{ id: 'q11.3', title: '11.3 Piirrä teleskoopin voimakuvio ja nimeä voimat.' },
	{ id: 'q11.4', title: '11.4 Teleskoopin etäisyys Maasta on 1,5 miljoonaa kilometriä. Perustele tämä osoittamalla, että Newtonin II laki toteutuu kyseisellä etäisyyden arvolla.' }
];

	const excludedCmds = [
		'searchAndReplace', 'bulletList', 'alignLeft', 'alignRight', 
		'audio-placeholder', 'taskList', 'orderedList', 'alignJustify', 
		'video-placeholder', 'iframe-placeholder', 'underline', 'subscript', 
		'heading1', 'heading2', 'bold', 'alignCenter', 'font increment', 'undo', 'redo', 'italic'
	];
</script>

<div style="max-width: 1000px; margin: 0 auto; padding: 20px;">
	<h1>Fysiikan Yo Kone</h1>
	<p style="color: #666; margin-bottom: 30px;">Each question has its own isolated editor. Data is automatically saved to localStorage.</p>

	{#each questions as question (question.id)}
		<div style="margin-bottom: 40px; padding: 20px; border: 1px solid #ddd; border-radius: 4px; background: #fafafa;">
			<h3 style="margin-top: 0; margin-bottom: 15px;">{question.title}</h3>
			<div style="width:auto; height:auto; border:1px solid #ddd;">
  <EditorWrapper editorId={question.id}
 excludedCommands={['searchAndReplace','bulletList','alignLeft','alignRight','audio-placeholder','taskList','orderedList','alignJustify','video-placeholder','iframe-placeholder','underline','subscript','heading1','heading2','bold','alignCenter','font increment','undo','redo','italic']} imagexasizewidth={500} imagemaxsizeheight={350} />
</div>
		</div>
	{/each}
</div>

<style>
	:global(body) {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
		background-color: #f5f5f5;
		margin: 0;
		padding: 0;
	}
</style>





