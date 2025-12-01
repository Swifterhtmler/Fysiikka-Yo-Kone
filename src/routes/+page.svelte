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
		{ id: 'K23 q4.0', title: 'K23: 4. Kondensaattori', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#4.A', label: '4' }, description: 'Aineisto: 4.A Kondensaattorin varautumis- ja purkautumiskäyrä, 4.B Täydennettävä piiri, 4.C Kytkin, 4.D Vastus, 4.E Jännitemittari. Kondensaattoria ensin varataan ja sen jälkeen kondensaattorin varausta puretaan.', isk23: true, isCompleted: false },
		{ id: 'K23 q4.1', title: 'K23: 4.1 Täydennä kuvan 4.B keskeneräinen kytkentäkaavio siten, että piirillä voisi tuottaa kuvan 4.A mukaisen kuvaajan. Käytä kahta kytkintä, johtimia, vastusta sekä jännitemittaria.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q4.2', title: 'K23: 4.2 Onko virran suunta kuvan 4.B pisteessä P ylös- vai alaspäin varautumiskäyrän ajanhetkillä t₁ ja t₂?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q4.3', title: 'K23: 4.3 Miten muuttaisit piirin komponentteja, jos haluat hidastaa kondensaattorin varautumista ja purkautumista?', description: '', isk23: true, isCompleted: false },

		// Section 2 - Question 5
		{ id: 'K23 q5.0', title: 'K23: 5. Kynttilä', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#5.A', label: '5' }, description: 'Aineisto: 5.A Mittausaineisto: Kynttilän pituus ajan funktiona, 5.B Valokuva maljakossa kelluvasta kynttilästä, 5.C Kynttilän voimakuvio. Kynttilää poltetaan ja sen pituus mitataan palamisajan funktiona. Kynttilän pituus alussa on 189 mm, halkaisija on 21 mm ja keskimääräinen tiheys on 862 kg/m³.', isk23: true, isCompleted: false },
		{ id: 'K23 q5.1', title: 'K23: 5.1 Laadi graafinen esitys kynttilän pituudesta ajan funktiona. Esitä graafissa aineiston pisteet ja mittausaineistoon sopiva malli.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q5.2', title: 'K23: 5.2 Toinen samanlainen kynttilä poltetaan täynnä vettä olevassa maljakossa, jossa kynttilä kelluu. Jotta kynttilä pysyisi pystyssä, sen tyveen kiinnitetään painoksi metallirengas, jonka massa on 3,5 g. Kuinka kauan kynttilä palaa maljakossa?', description: '', isk23: true, isCompleted: false },

		// Section 2 - Question 6
		{ id: 'K23 q6.0', title: 'K23: 6. Sipsipussin rapistelu', material: { }, description: 'Yhdysvaltalainen yritys toi vuonna 2010 markkinoille biohajoavan Sun Chips -perunalastupussin. Pussin ongelmana oli voimakas rapisteluääni, jonka intensiteettitaso ylsi peräti 95 desibeliin. Oletetaan, että intensiteettitaso mitattiin 1,0 metrin etäisyydeltä.', isk23: true, isCompleted: false },
		{ id: 'K23 q6.1', title: 'K23: 6.1 Mikä on intensiteettitaso, kun viisi ihmistä rapistelee kukin omaa sipsipussiaan samanaikaisesti 1,0 metrin etäisyydellä mittarista?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q6.2', title: 'K23: 6.2 Tuotekehityksellä rapisteluäänen intensiteettitaso saatiin laskettua 75 desibeliin. Kuinka monta prosenttia äänen intensiteetti oli tällöin alkuperäisestä intensiteetistä?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q6.3', title: 'K23: 6.3 Arvioi, millä etäisyydellä alkuperäisen sipsipussin intensiteettitaso (95 dB) vastaa tuulen huminaa, jonka intensiteettitaso on 30 dB.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q6.4', title: 'K23: 6.4 Miksi osatehtävässä 6.3 laskettu etäisyyden arvio ei ole realistinen käytännön tilanteessa?', description: '', isk23: true, isCompleted: false },

		// Section 2 - Question 7
		{ id: 'K23 q7.0', title: 'K23: 7. Käsikäyttöinen generaattori', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#7.A', label: '7' }, description: 'Aineisto: 7.A Kuva: Käsikäyttöinen generaattori, 7.B Simulaatio generaattorin tuottamasta jännitteestä. Kun kestomagneetin sisällä oleva käämi pyörii tasaisella kulmanopeudella, syntyy johtimien välille jaksollisesti vaihteleva jännite.', isk23: true, isCompleted: false },
		{ id: 'K23 q7.1', title: 'K23: 7.1 Selitä, miten jännite syntyy.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q7.2', title: 'K23: 7.2 Johda induktiolaista lähtien lauseke |e|=NBAω käämiin indusoituvan jännitteen huippuarvolle. Lausekkeessa N on käämin kierroslukumäärä, B kestomagneetin magneettivuon tiheys, A käämin pinta-ala ja ω käämin kulmanopeus.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q7.3', title: 'K23: 7.3 Simulaatio generaattorin tuottamasta jännitteestä on aineistossa 7.B. Neliön muotoisessa käämissä on 150 kierrosta ja käämin sivun pituus on 6 cm. Määritä simulaation avulla magneettivuon tiheys käämin kohdalla.', description: '', isk23: true, isCompleted: false },

		// Section 2 - Question 8
		{ id: 'K23 q8.0', title: 'K23: 8. Pieni Curie', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#8.A', label: '8' }, description: 'Aineisto: 8.A Artikkeli: "Marie Curie laboratoriossa ja rintamalla", 8.B Valokuva fluoroskopiakuvantamisesta ensimmäisen maailmansodan ajalta, 8.C Röntgenkuva influenssapotilaan keuhkoista vuodelta 1918. Artikkeli kuvaa ensimmäisessä maailmansodassa käytettyjä siirrettäviä röntgenkuvauslaitteita.', isk23: true, isCompleted: false },
		{ id: 'K23 q8.1', title: 'K23: 8.1 Miksi röntgenlaitteita ei tuolloin voitu useinkaan kytkeä suoraan sähköverkkoon?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q8.2', title: 'K23: 8.2 Säteily voitiin havaita kuvalevyllä tai fluoroskoopilla. Kumpaa tapaa käyttäisit itse nykypäivänä ja miksi?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q8.3', title: 'K23: 8.3 Miksi aineistossa 8.A kuvattuja vammoja tai keuhkosairauksia voidaan havaita röntgenkuvantamisella?', description: '', isk23: true, isCompleted: false },

		// Section 3 - Question 9
		{ id: 'K23 q9.0', title: 'K23: 9. Gammasäteilyn ja aineen välinen vuorovaikutus', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#9.A', label: '9' }, description: 'Aineisto: 9.A Todennäköisin fotonin vuorovaikutustapa eri energioilla ja alkuaineen järjestysluvuilla, 9.B Kahden eri ilmaisimen tuottamat energiaspektrit 662 keV:n gammalähteelle. Gammafotoni eli korkeaenergiainen fotoni vuorovaikuttaa aineen kanssa kolmella eri tavalla.', isk23: true, isCompleted: false },
		{ id: 'K23 q9.1', title: 'K23: 9.1 Mitä fotonille tapahtuu, ja mihin sen energia siirtyy valosähköilmiössä ja parinmuodostuksessa?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q9.2', title: 'K23: 9.2 Comptonin ilmiössä fotoni siroaa elektronista. Mikä on suurin liike-energia, jonka elektroni voi saada fotonilta, kun 662 keV:n fotoni siroaa siitä?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q9.3', title: 'K23: 9.3 Kahdella erilaisella tilavuudeltaan pienellä ilmaisimella havaittiin Cs-137-säteilylähteen tuottamaa 662 keV:n gammasäteilyä. Selitä, mitä on todennäköisimmin tapahtunut ilmaisimissa, kun spektreihin on ilmaantunut tapahtumia alle 400 keV:n alueelle. Kumpi kuvan 9.B spektreistä (A/B) on muovista valmistetun ilmaisimen spektri?', description: '', isk23: true, isCompleted: false },

		// Section 3 - Question 10
		{ id: 'K23 q10.0', title: 'K23: 10. Parafiinin sulamislämpö', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#10.A', label: '10' }, description: 'Aineisto: 10.A Piirrospohja. Haluat kokeellisesti määrittää materiaalin ominaissulamislämmön fysiikan oppitunnilla. Olet valinnut materiaaliksi parafiinin, jonka sulamispiste on 60 °C. Käytettävissä: solupolystyreeniastia, vettä ja vedenkeitin, kiinteätä parafiinia 20 °C:ssa, sekä fysiikan luokan mittausvälineet.', isk23: true, isCompleted: false },
		{ id: 'K23 q10.1', title: 'K23: 10.1 Mitkä ovat työn päävaiheet ja niissä tehtävät mittaukset? Miten määrität mittaustuloksista parafiinin ominaissulamislämmön? Esitä tarvittavat suureyhtälöt. Mitkä numeroidun listan välineistä tarvitset?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q10.2', title: 'K23: 10.2 Vertaat lopuksi mittauksista saamaasi sulamislämmön arvoa kirjallisuusarvoon. Luettele kolme tärkeätä tekijää, jotka aiheuttavat mittaamaasi arvoon poikkeaman kirjallisuusarvosta.', description: '', isk23: true, isCompleted: false },

		// Section 3 - Question 11
		{ id: 'K23 q11.0', title: 'K23: 11. James Webb -avaruusteleskooppi', material: { url: 'https://yle.fi/plus/abitreenit/2023/kevat/2023-03-24_FY_fi/attachments/index.html#11.A', label: '11' }, description: 'Aineisto: 11.A James Webb -avaruusteleskooppi, 11.B Aurinko-Maa-järjestelmän Lagrangen piste L2. Joulupäivänä 2021 laukaistiin James Webb -avaruusteleskooppi Lagrangen pisteeseen L2. Teleskooppi kiertää Aurinkoa pysyen Auringon ja Maan kautta kulkevalla suoralla. Teleskooppi toimii lähinnä infrapuna-alueella.', isk23: true, isCompleted: false },
		{ id: 'K23 q11.1', title: 'K23: 11.1 Miksi alhainen lämpötila on olennainen tekijä infrapunasäteilyn havainnoinnissa?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q11.2', title: 'K23: 11.2 Miksi kuvassa 11.A näkyvä teleskoopin lämpösuoja ei ole yhtenäinen kerros, vaan koostuu viidestä erillään olevasta kerroksesta?', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q11.3', title: 'K23: 11.3 Piirrä teleskoopin voimakuvio ja nimeä voimat.', description: '', isk23: true, isCompleted: false },
		{ id: 'K23 q11.4', title: 'K23: 11.4 Teleskoopin etäisyys Maasta on 1,5 miljoonaa kilometriä. Perustele tämä osoittamalla, että Newtonin II laki toteutuu kyseisellä etäisyyden arvolla.', description: '', isk23: true, isCompleted: false },
	   
		// syksy 2022 koe

		{ 
		id: 'S22 q2.0', 
		title: 'S22: 2. Astronautin hyppy',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#2',
			label: '2.A, 2.B'
		},
		description: 'Astronautti John Young hyppäsi vuonna 1972 Kuun pinnalla lähes pystysuoran hypyn ylöspäin. Videoidusta hypystä määritettiin astronautin repun yläosan etäisyys Kuun pinnasta ajan funktiona.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q2.1', 
		title: 'S22: 2.1 Laadi graafinen esitys määritetystä etäisyydestä ajan funktiona.',
		description: 'Esityksessä tulee näkyä mittauspisteet ja niihin sopiva, fysikaalisen mallin mukainen sovite. Mistä liikkeen mallista on kyse?',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q2.2', 
		title: 'S22: 2.2 Millä ajanhetkellä John Young on hyppynsä korkeimmassa kohdassa?',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q2.3', 
		title: 'S22: 2.3 Määritä aineiston perusteella putoamiskiihtyvyys Kuun pinnalla.',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 3
	{ 
		id: 'S22 q3.0', 
		title: 'S22: 3. Vastapainohissi',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#3',
			label: '3.A'
		},
		description: 'Yksinkertaisen vastapainohissin hissikorin ja siinä olevan kuorman yhteismassa on 830 kg ja vastapainon massa 670 kg. Hissi lähtee liikkeelle ylöspäin, ja sen nopeus kasvaa 1,2 sekunnissa tasaisesti nollasta arvoon 1,6 m/s.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q3.1', 
		title: 'S22: 3.1 Määritä hissivaijerin hissikoriin ja vastapainoon kiihdytyksen aikana kohdistamat voimat.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q3.2', 
		title: 'S22: 3.2 Kuinka suuria ovat hissin nopeus ja moottorin tuottama mekaaninen teho, kun hissin liikkeellelähdöstä on kulunut 0,80 sekuntia?',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 4
	{ 
		id: 'S22 q4.0', 
		title: 'S22: 4. Kirurginen polttolaite',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#4',
			label: '4.A'
		},
		description: 'Kirurgista diatermialaitetta eli polttolaitetta käytetään muun muassa luomien poistossa sekä verenvuotojen tyrehdyttämisessä. Polttoprosessissa laitteella johdetaan korkeataajuuksista vaihtovirtaa kudosalueen läpi. Tarkastellaan kirurgista toimenpidettä, jossa käytettävä diatermialaite tuottaa sinimuotoista vaihtovirtaa 58 watin teholla.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q4.1', 
		title: 'S22: 4.1 Toimenpiteessä lämmitetään ensin 1,1 g kudosnestettä ruumiinlämmöstä (37 °C) kiehumispisteeseen. Tämän jälkeen 0,40 g tästä kudosnesteestä höyrystyy. Kuinka kauan toimenpide kestää?',
		description: 'Kudosneste on pääosin vettä.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q4.2', 
		title: 'S22: 4.2 Tehollinen sähkövirta kudoksessa on 0,45 ampeeria. Kuinka suuri on jännitteen huippuarvo?',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q4.3', 
		title: 'S22: 4.3 Kuinka suuri on poltettavan kudosalueen resistanssi toimenpiteen aikana?',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 5
	{ 
		id: 'S22 q5.0', 
		title: 'S22: 5. Varatut kuulat',
		material: { },
		description: 'Kaksi identtistä pientä sähköisesti varattua alumiinikuulaa pidetään aluksi 0,10 metrin etäisyydellä toisistaan. Kuulat vetävät toisiaan puoleensa 1,0 newtonin voimilla. Kuulien annetaan koskettaa toisiaan, minkä jälkeen ne siirretään takaisin 0,10 metrin etäisyydelle. Kuulien väliset voimat ovat edelleen 1,0 newtonia, mutta nyt kuulat hylkivät toisiaan.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q5.1', 
		title: 'S22: 5.1 Miksi kuulat vetävät toisiaan puoleensa ennen kosketusta? Miksi kosketus saa kuulat hylkimään toisiaan?',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q5.2', 
		title: 'S22: 5.2 Määritä, mitkä olivat kuulien varaukset ennen kuin kuulat koskettivat toisiaan.',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 6
	{ 
		id: 'S22 q6.0', 
		title: 'S22: 6. Sähkömagneettinen induktio',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#6',
			label: '6.A'
		},
		description: 'Kaikissa alla olevissa tapauksissa 6.1–6.5 neliön muotoinen johdinsilmukka on äärellisen kokoisessa homogeenisessa magneettikentässä. Valitse kussakin tapauksessa se aineiston 6.A kuvaaja A–H, joka parhaiten kuvaa silmukkaan indusoituvaa sähkövirtaa ajan funktiona.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q6.1', 
		title: 'S22: 6.1 Silmukkaa pyöritetään vakiokulmanopeudella silmukan pyörimisakselin ollessa kohtisuorassa kenttää vastaan.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q6.2', 
		title: 'S22: 6.2 Silmukkaa pyöritetään vakiokulmanopeudella silmukan pyörimisakselin ollessa kentän suuntainen.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q6.3', 
		title: 'S22: 6.3 Silmukka on alussa paikallaan magneettikentän alueella. Silmukka päästetään putoamaan vapaasti nuolen suuntaan.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q6.4', 
		title: 'S22: 6.4 Silmukka on paikallaan. Magneettikenttä häviää äkillisesti.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q6.5', 
		title: 'S22: 6.5 Silmukka on paikallaan. Magneettikentän magneettivuon tiheys vuoron perään kasvaa ja heikkenee tasaisesti.',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 7
	{ 
		id: 'S22 q7.0', 
		title: 'S22: 7. Peltipurkkipuhelin',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#7',
			label: '7.A'
		},
		description: 'Yksinkertaisen peltipurkkipuhelimen rakenne. Vastaavanlainen peltipurkkipuhelin rakennettiin käyttäen kahta peltipurkkia ja 75 metriä pitkää messinkilankaa.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q7.1', 
		title: 'S22: 7.1 Millaisena mekaanisena aaltoliikkeenä ääni etenee peltipurkkipuhelimen langassa?',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q7.2', 
		title: 'S22: 7.2 Kuinka paljon aiemmin ääni saavuttaa kuulijan, kun käytetään peltipurkkipuhelinta pelkän huutamisen sijaan?',
		description: 'Äänen nopeudelle ohuessa messinkilangassa pätee yhtälö v = √(E/ρ), jossa E = 10,5·10¹⁰ N/m² on messingin kimmokerroin ja ρ = 8,4·10³ kg/m³ tiheys. Äänen nopeus ilmassa (lämpötila 20 °C) on 343 m/s.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q7.3', 
		title: 'S22: 7.3 Laske äänen intensiteettitaso kuulijan peltipurkin pohjan kohdalla.',
		description: 'Peltipurkkipuhelimessa ääni vaimenee merkittävästi ainoastaan messinkilangassa tapahtuvan absorption takia. Vaimenemiselle pätee yhtälö I = I₁e^(-αx), jossa I₁ on äänen intensiteetti lähteessä, I on äänen intensiteetti etäisyydellä x lähteestä ja α = 0,086 m⁻¹ on messinkilangassa etenevän äänen vaimenemiskerroin. Puhujan äänen intensiteettitaso on 72 dB puhujan peltipurkin pohjan kohdalla 7,0 cm:n etäisyydellä puhujan suusta. Laske myös äänen intensiteettitaso 75 m:n etäisyydellä, jos puhuja puhuu samalla äänen voimakkuudella ilman peltipurkkipuhelinta. Vertaile tuloksia keskenään.',
		iss22: true,
		isCompleted: false
	},

	// Section 2 - Question 8
	{ 
		id: 'S22 q8.0', 
		title: 'S22: 8. Hiiliajoitus',
		material: { },
		description: 'Hiili esiintyy luonnossa kahtena pysyvänä isotooppina ¹²C ja ¹³C sekä radioaktiivisena isotooppina ¹⁴C. Ilmakehässä isotoopin ¹²C lukumääräosuus on 98,9 % ja isotoopin ¹³C lukumääräosuus on 1,1 %. Isotoopin ¹⁴C osuus kaikesta ilmakehän hiilestä on 1,2·10⁻¹², ja isotoopin puoliintumisaika on 5 730 vuotta.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q8.1', 
		title: 'S22: 8.1 Kirjoita isotoopin ¹⁴C syntymisen ja hajoamisen reaktioyhtälöt.',
		description: 'Isotooppi ¹⁴C syntyy ilmakehässä, kun typpiydin ¹⁴N sieppaa kosmisen säteilyn synnyttämän neutronin ja säteilee samalla protonin. ¹⁴C hajoaa β⁻-hajoamisella.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q8.2', 
		title: 'S22: 8.2 Selitä lyhyesti, mihin radiohiiliajoitus perustuu.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q8.3', 
		title: 'S22: 8.3 Arvioi, kuinka kauan aikaa sitten asuinpaikkaa käytettiin.',
		description: 'Eräästä Itä-Suomessa sijaitsevasta kivikautisesta asuinpaikasta löytyi kaivauksissa nisäkkään luu, jolle tehtiin massaspektrometrillä hiilen isotooppisuhteiden määritys. Isotooppien ¹⁴C ja ¹³C lukumääräsuhteeksi saatiin 3,5·10⁻¹¹.',
		iss22: true,
		isCompleted: false
	},

	// Section 3 - Question 9
	{ 
		id: 'S22 q9.0', 
		title: 'S22: 9. Diodi',
		material: { },
		description: '',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q9.1', 
		title: 'S22: 9.1 Kerro, kuinka diodi käyttäytyy virtapiirissä. Mihin diodeja käytetään?',
		iss22: true,
		isCompleted: false

	},
	{ 
		id: 'S22 q9.2', 
		title: 'S22: 9.2 Suunnittele ja kuvaile mittaus, jolla voit määrittää tuntemattoman diodin ominaiskäyrän.',
		description: 'Sinulla on käytössäsi diodin lisäksi johtimia, jännitemittari, välillä 0–5 V säädettävä tasajännitelähde sekä useita erilaisia vastuksia, joiden resistanssit tunnetaan. Millaisen ominaiskäyrän oletat saavasi tulokseksi?',
		iss22: true,
		isCompleted: false
	},

	// Section 3 - Question 10
	{ 
		id: 'S22 q10.0', 
		title: 'S22: 10. Saippuakuplat',
		material: { },
		description: 'Fyysikko rentoutuu puhaltelemalla saippuakuplia puutarhakeinussaan.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q10.1', 
		title: 'S22: 10.1 Selitä, miksi heijastuneessa valossa näkyy eri värejä.',
		description: 'Auringonvalo heijastuu kuplien pinnoista.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q10.2', 
		title: 'S22: 10.2 Selitä, miksi kuplan värit vähitellen haalistuvat ja juuri ennen kuplan puhkeamista häviävät miltei kokonaan.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q10.3', 
		title: 'S22: 10.3 Miksi saippuakupla puhkeaa? Miksi isot kuplat puhkeavat nopeammin kuin pienet kuplat?',
		description: 'Saippuakupla puhkeaa yleensä muutamassa minutissa. Samasta määrästä nestettä voidaan puhaltaa erikokoisia kuplia.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q10.4', 
		title: 'S22: 10.4 Määritä näillä tiedoilla kuplan kalvon paksuus.',
		description: 'Fyysikko huomaa, että yksi kuplista leijuu paikallaan tyynessä ilmassa. Saippuaveden tiheydeksi oletetaan 1,0·10³ kg/m³ ja kuplan sisällä olevan ilman lämpötilaksi 26 °C. Ulkoilman lämpötila on 21 °C ja kuplan säde 5,0 cm. Ilman oletetaan olevan 79 % typpeä ja 21 % happea myös kuplan sisällä.',
		iss22: true,
		isCompleted: false
	},

	// Section 3 - Question 11
	{ 
		id: 'S22 q11.0', 
		title: 'S22: 11. Juoman jäähdyttäminen',
		material: {
			url: 'https://yle.fi/plus/abitreenit/2022/Syksy/2022-09-22_FY_fi/attachments/index.html#11',
			label: '11.A'
		},
		description: 'Artikkelissa esitellään kolme käytännön koetta ja yksi ajatuskoe erilaisten juomien jäähdyttämisestä.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q11.1', 
		title: 'S22: 11.1 Miksi juomat jäähtyvät eri tahtiin?',
		description: 'Ensimmäisessä kokeessa kolme juomaa laitetaan jääkaappiin.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q11.2', 
		title: 'S22: 11.2 Miksi paperikääre tehostaa jäähtymistä parvekkeella enemmän kuin jääkaapissa?',
		description: 'Toisessa kokeessa juomat kääritään märkään paperiin.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q11.3', 
		title: 'S22: 11.3 Miksi jääkylpy viilentää juomia nopeasti, ja miksi suolan lisääminen vaikuttaa viilenemisnopeuteen?',
		description: 'Kolmannessa kokeessa juomat viilennetään jääkylvyssä.',
		iss22: true,
		isCompleted: false
	},
	{ 
		id: 'S22 q11.4', 
		title: 'S22: 11.4 Kuinka korkea putken pitäisi olla, jotta juoma voitaisiin jäähdyttää lämpötilaan 9 °C?',
		description: 'Viimeisenä esitetään ajatuskoe, jossa litra olutta (T = 25 °C) jäähdytetään putkessa. Oleta, että putken säde on 6 cm. Voit olettaa, että juoma vastaa ominaisuuksiltaan vettä ja vain pieni osa vedestä höyrystyy.',
		iss22: true,
		isCompleted: false
	},

	// kevät 2024 koe

	{
    "id": "K24 q2.0",
    "title": "K24: 2. Omenamehupuristin",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#2",
      "label": "2.A, 2.B"
    },
    "description": "Omenamehupuristimella (kuva 2.A) tehdään omenoista tuoremehua. Puristimen kampea kierrettiin yksi kierros kerrallaan ja ulos valuneen mehun tilavuus mitattiin (aineisto 2.B).",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q2.1",
    "title": "K24: 2.1 Esitä graafisesti mehun tilavuus männän ylimmästä asemastaan liikkuman matkan funktiona. Yksi kammen kierros vastaa 4,0 mm:n pystysuoraa liikettä.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q2.2",
    "title": "K24: 2.2 Määritä osatehtävässä 2.1 piirtämääsi kuvaajaa pohjana käyttäen, kuinka paljon mehua omenoista saatiin ennen kuin mäntä saavutti murskeen.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q2.3",
    "title": "K24: 2.3 Omenoiden puristusta jatkettiin 79 kierrosta. Mehua saatiin samassa suhteessa tilavuuden pienenemiseen verrattuna. Arvioi graafista esitystä käyttäen, kuinka paljon mehua omenoista kokonaisuudessaan saatiin.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q3.0",
    "title": "K24: 3. Uudenvuodentinojen valaminen",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#3",
      "label": "3.A, 3.B"
    },
    "description": "Uudenvuodenperinteessä sulaa ainetta kaadetaan kylmään veteen. Lyijyn sijaan käytetään joskus kidesokeria (aineisto 3.A). Videolla 3.B sulatetaan lyijyä ja sokeria.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q3.1",
    "title": "K24: 3.1 Osoita, että kidesokerin sulattamiseen tarvitaan 8,2 kJ energiaa, jos huoneenlämpöistä (21°C) sokeria otetaan kaksi ruokalusikallista (30 ml).",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q3.2",
    "title": "K24: 3.2 Osatehtävän 3.1 sokerimäärä sulatetaan levyllä, jonka teho on 1 200 W. Sulaminen kestää 2,5 minuuttia. Määritä sulattamisen hyötysuhde.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q3.3",
    "title": "K24: 3.3 Video 3.B esittää lyijyn ja sokerin kuumentamista. Lyijy sulaa nopeasti, mutta osa sokerista ei sula pitkään aikaan. Mistä ero johtuu?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q4.0",
    "title": "K24: 4. Voimat",
    "material": {},
    "description": "Valitse osatehtävien tilanteissa voimakuvioista A–D se, joka kuvaa parhaiten tarkasteltavaan kappaleeseen vaikuttavia ulkoisia voimia. Kappale liikkuu kaikissa tilanteissa oikealle. Nimeä voimakuvioon piirretyt voimat.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q4.1",
    "title": "K24: 4.1 Ilmassa lentävä nuoli.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q4.2",
    "title": "K24: 4.2 Heiton jälkeen jään pinnalla liukuva curling-kivi.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q4.3",
    "title": "K24: 4.3 Uimarin selkään hihnalla kiinnitetty, vedessä liikkuva uimapoiju.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q5.0",
    "title": "K24: 5. Eksoplaneetan kiertoaika",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#5",
      "label": "5.A, 5.B, 5.C"
    },
    "description": "Eksoplaneetta voidaan löytää, kun tähden valon intensiteetti pienenee planeetan kulkiessa tähden editse (kuva 5.A). Aineistossa 5.B on tähden intensiteetin vaihtelu ja 5.C pohja voimakuviolle.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q5.1",
    "title": "K24: 5.1 Kuinka monta prosenttia tähden pinta-alasta planeetta enimmillään peittää (kuva 5.B)?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q5.2",
    "title": "K24: 5.2 Määritä kuvan 5.B avulla tähteä kiertävän eksoplaneetan kiertoaika.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q5.3",
    "title": "K24: 5.3 Täydennä eksoplaneetan voimakuvio (5.C). Laske ympyräradan säde, kun tähden massa on 1,52 kertaa Auringon massa.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q6.0",
    "title": "K24: 6. Pölyhiukkanen kondensaattorissa",
    "material": {},
    "description": "Levykondensaattorin levyjen väli 2,6 mm, jännite 36 V. Positiiviselta levyltä irtoaa pölyhiukkanen (massa 3,3 mg, varaus 5,7 pC).",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q6.1",
    "title": "K24: 6.1 Kuinka suuri on sähkökentän voimakkuus levyjen välissä, ja minkä suuntainen se on?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q6.2",
    "title": "K24: 6.2 Kuinka suuri on pölyhiukkaseen kohdistuva sähköinen voima?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q6.3",
    "title": "K24: 6.3 Tarkastellaan vain sähköistä voimaa. Millaista hiukkasen liike on? Kuinka kauan kestää matka negatiiviselle levylle levosta?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q7.0",
    "title": "K24: 7. Leijulauta",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#7",
      "label": "7.A"
    },
    "description": "Esiteltiin leijulaudan prototyyppi, jolla voi leijailla kuparilattian päällä (kuva 7.A). Laudan sisällä moottorit pyörittävät kestomagneetteja.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q7.1",
    "title": "K24: 7.1 Miksi leijulaudan pyörivät magneetit mahdollistavat leijumisen kuparilattian päällä?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q7.2",
    "title": "K24: 7.2 Miksi leijuminen ei onnistu asfaltin päällä?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q7.3",
    "title": "K24: 7.3 Mitä voimia lautaan vaikuttaa kuvan 7.A tilanteessa?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q7.4",
    "title": "K24: 7.4 Miksi lattia lämpenee, vaikka lauta ei kosketa lattiaa?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q8.0",
    "title": "K24: 8. Ydinvoimalaitos Olkiluoto 3",
    "material": {},
    "description": "Olkiluoto 3 tuottaa sähköä 1 600 MW:n teholla, hyötysuhde 0,375. Se käy 330 vrk vuodessa. Energiantuotanto perustuu uraanin fissioon, jossa vapautuu 0,20 GeV energiaa per reaktio.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q8.1",
    "title": "K24: 8.1 Kuinka monta fissioreaktiota tapahtuu sekunnissa Olkiluoto 3:ssa täydellä teholla?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q8.2",
    "title": "K24: 8.2 Kuinka paljon polttoaineen massaa katoaa fissioreaktioiden takia vuodessa?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q8.3",
    "title": "K24: 8.3 Jos sama sähköteho tuotettaisiin kivihiilellä, hiiltä tarvittaisiin 100 000-kertainen massa uraaniin verrattuna. Mistä tämä ero johtuu?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q8.4",
    "title": "K24: 8.4 Kuvaile kolme merkittävää eroa hiilivoimalan ja ydinvoimalan välillä käytön aikaisissa haitoissa ja riskeissä.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q9.0",
    "title": "K24: 9. Aurinkovoimala",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#9",
      "label": "9.A, 9.B"
    },
    "description": "Aineistossa 9.A on esitetty 18 aurinkopaneelin pienvoimalan sähköteho 3.8.2022. Taulukossa 9.B on sähköteho ajan funktiona useana päivänä.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q9.1",
    "title": "K24: 9.1 Mainitse kolme muuta asiaa (kuin auringon nousu/lasku), jotka vaikuttavat energiantuotannon muutokseen vuorokauden mittaan.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q9.2",
    "title": "K24: 9.2 Kuinka paljon energiaa pienvoimala pystyisi enimmillään tuottamaan yhdessä vuorokaudessa elokuun alussa? Laadi taulukon 9.B perusteella graafinen esitys ja määritä energia.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q9.3",
    "title": "K24: 9.3 Mihin aikaan päivästä ja kuinka pitkällä aikavälillä paneelien energiantuotanto olisi suurimmillaan ideaalitilanteessa (9.2)?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q9.4",
    "title": "K24: 9.4 Paneelien hyötysuhde on 19 %. Mainitse kaksi seikkaa, jotka vaikuttavat siihen, että kaikkea säteilyenergiaa ei voida muuttaa sähköenergiaksi.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q10.0",
    "title": "K24: 10. Autorata",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#10",
      "label": "10.A, 10.B"
    },
    "description": "Leikkiauto (37 g) kulkee radalla, jossa on kolme pystysuoraa silmukkaa (halkaisijat 51, 38, 25 cm) ja hyppyri (video 10.A, kuva 10.B).",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q10.1",
    "title": "K24: 10.1 Auto kulkee radan korkeimmassa kohdassa ylösalaisin. Mikä on sen pienin mahdollinen nopeus tässä kohdassa?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q10.2",
    "title": "K24: 10.2 Auto lähetetään nopeudella 3,1 m/s. Se lennähtää hyppyristä 32 cm:n korkeuteen ja laskeutuu (kuva 10.B). Kuinka suuri oli vastusvoimien tekemä työ koko radan matkalla?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q10.3",
    "title": "K24: 10.3 Auto ohittaa ensimmäisen ja toisen silmukan pienimmillä mahdollisilla nopeuksilla. Pääseekö se kolmannen silmukan läpi? Oleta vastusvoimien olevan keskimäärin yhtä suuria kaikissa silmukoissa.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q11.0",
    "title": "K24: 11. Röntgendiffraktio ja elektronidiffraktio",
    "material": {
      "url": "https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/attachments/index.html#11",
      "label": "11.A, 11.B"
    },
    "description": "Teksti (11.A) kuvaa röntgen- ja elektronidiffraktion käyttöä kiteen rakenteen tutkimuksessa. Kuvaaja (11.B) esittää raudasta mitatun röntgendiffraktiokuvaajan.",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q11.1",
    "title": "K24: 11.1 Johda aineiston 11.A kuvaa apuna käyttäen Braggin laki 2d sin θ = nλ.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q11.2",
    "title": "K24: 11.2 Kuvassa 11.B on raudasta mitattu röntgendiffraktiokuvaaja (λ = 0,15406 nm). Mikä intensiteettimaksimeista (a, b, c) vastaa pienintä atomitasojen välistä etäisyyttä? Määritä etäisyys.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q11.3",
    "title": "K24: 11.3 Kokeessa käytetään röntgensäteilyä (energia 17,48 keV). Toisessa kokeessa käytetään elektroneja. Määritä elektronien nopeus (% valon nopeudesta), kun de Broglien aallonpituus on sama.",
    "description": "",
    "isK24": true,
	 isCompleted: false
  },
  {
    "id": "K24 q11.4",
    "title": "K24: 11.4 Kuinka suuri kiihdytysjännite tarvitaan elektronien kiihdyttämiseksi osatehtävässä 11.3 kysyttyyn nopeuteen?",
    "description": "",
    "isK24": true,
	 isCompleted: false
  }

	];

	let currentQuestionIndex = 0;
	$: currentQuestion = questions[currentQuestionIndex];
 //  let isCorrect = false;
	
   function checkAnswer() {
		
		currentQuestion.isCompleted = true;

		if (currentQuestion.isk23 == true) {
		window.open("https://drive.google.com/file/d/17eKbwTU-_cnZQSHAPCZHD81LxaisM_zk/view?pli=1", '_blank').focus();
		} else if (currentQuestion.iss22 == true) {
         window.open("https://drive.google.com/file/d/12UxfOG6F7nIE2wsc9GG8gDgxF0t-UXdE/view", '_blank').focus();
		} else if (currentQuestion.isK24 == true) {
         window.open("https://yle.fi/plus/abitreenit/2024/kevat/fysiikka/fysiikka_hvp_lopulliset.pdf", '_blank').focus();
		}
	}


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
		<button id="checkButton" on:click={checkAnswer}>Katso vastaus</button>
	</div>

	<!-- Navigation buttons -->
	<div class="navigation">
		<button 
			class="nav-button" 
			on:click={previousQuestion} 
			disabled={currentQuestionIndex === 0}
		>
			← Edellinen
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
			Seuraava →
		</button>
	</div>

	<!-- Question grid for quick navigation -->
	<div class="question-grid">
		{#each questions as question, index}
			<button 
				class="question-number" 
				class:active={index === currentQuestionIndex}
				class:incomplete={question.isCompleted === false}
				class:completed={question.isCompleted === true}
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

	.question-number.incomplete {
		background-color: #8a8383;
		color: white;
		border-color: #413f3f;
	}

	.question-number.incomplete:hover {
		border-color: #4CAF50;
		background-color: #1a1a1a;
	}

	.question-number.completed {
		background-color: #e8f5e9;
		color: #2e7d32;
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

	#checkButton {
	 border: 1px solid black;
	 margin-top: 8px;
	 text-align: center;
	 border-radius: 8px;
	 color: #f1f8f4;
	 background-color: #4CAF50;
	 padding: 8px;
	}

	#checkButton:hover {
		border: 1px solid white;
		margin-top: 8px;
		text-align: center;
		border-radius: 8px;
		color: #f1f8f4;
		background-color: #09eb11;
		padding: 8px;
	}




</style>