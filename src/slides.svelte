<script lang="ts">
	import { Presentation, Slide, Notes } from '@components'
	import Layout from './layout.svelte'
</script>

<!-- Typical Errors
	
	"Uncaught TypeError: slidesInChapter[0] is undefined" and layout elements missing.
	→ This can happen if a chapter is defined but has no slides.

-->

<Presentation>
	<style>
		.textStyle ul {
			list-style: none;
			padding: 0;
			margin: 0;
		}

		.textStyle li {
			margin-bottom: 10px; /* optional: Hinzufügen von vertikalem Abstand zwischen den Listenelementen */
			font-size: 6vh;
		}
	</style>

	<script>
		// information about this presentation
		const author = 'Raman Ahmad'
		const authorshort = 'Raman Ahmad'
		const title = 'Energieverbrauch von Anwendungen'
		const subtitle = 'Maschinelles Lernen'
		const department = 'Hochscuhle für Angewandte Wissenschaften HAW'
		const university =
			'Informatik Seminar Bachelor, SoSe 24 </br>Jan Sudeikat & Michael Köhler-Bußmeier'
		var currentChapterName = ''
		var currentChapterNumber = 0
		var chapterNames = []
		var toc = false // whether toc is to be generated
		// data structure: [chapter number, chapter name, slideID]
		var presentationData = []
		function newChapter(chapterName) {
			currentChapterName = chapterName
			currentChapterNumber++
			chapterNames.push(chapterName)
		}
		// called when new slide is created
		var page = 0
		function newPage() {
			page++ //note that page n has index n-1
			presentationData.push({
				chapternr: currentChapterNumber,
				chapter: currentChapterName,
				pagenr: page,
			})
		}
	</script>

	<!-- title page -->
	<Slide
		><Layout>
			<div
				class="m-16 flex h-[25vh] w-[90vw] bg-[var(--themecolor)] text-white items-center justify-center gap-[100px]"
			>
				<div>
					<div class="text-[8vh]">
						<span id="mytitle"> </span>
					</div>
					<br />
					<div class="text-[6vh]">
						<span id="mysubtitle"> </span>
					</div>
				</div>
			</div>
			<div class="text-[6vh]">
				<span id="myname"></span>
			</div>
			<br />
			<div class="text-[4vh]">
				<span id="myuni"></span>
			</div>
			<div class="text-[3.5vh]">
				<br />
				<span id="mydate"></span>
			</div>
			<br />
			<!-- 
		<div class="flex items-center justify-center">
			<img class="h-[15vh] align-middle" src="title-logo.png" alt="tum logo">
		</div>
		-->
			<!-- fill in the data for this presentation  -->
			<!-- fill in the data for this presentation  -->
			<!-- fill in the data for this presentation  -->
			<!-- fill in the data for this presentation  -->
			<!-- fill in the data for this presentation  -->
			<!-- fill in the data for this presentation  -->
			<script>
				document.getElementById('mytitle').innerHTML = title
				document.getElementById('mysubtitle').innerHTML = subtitle
				document.getElementById('myname').innerHTML = author
				document.getElementById('myuni').innerHTML =
					department + '<br>' + university
				let today = new Date()
				document.getElementById('mydate').innerHTML = today
					.toISOString()
					.split('T')[0]
			</script>
		</Layout></Slide
	>
	<!-- TOC -->
	<!-- <Slide>
		<script>
			toc=false; // decides whether to generate table of content page
		</script>
		<Layout>
			<toc class="flex h-full items-center justify-center gap-[100px]">
				<chpicons> </chpicons>
				<chpnames class="text-left"> </chpnames>
			</toc>
		</Layout>
	</Slide> -->

	<!-- intro -->

	<!-- intro -->
	<!-- intro -->
	<!-- intro -->
	<!-- intro -->
	<!-- intro -->
	<script>
		newChapter('Gliederung')
	</script>
	<Slide>
		<Layout>
			<titlebar>Gliederung</titlebar>
			<mybody class="textStyle">
				<ul>
					<li>1. Maschinelles Lernen</li>
					<li>2. Rechenzentren und Energieverbrauch</li>
					<li>3. Energieverbrauch in der KI</li>
					<li>4. Stromverbrauch von GPT-Modellen</li>
					<li>5. Schlussfolgerung</li>
					<li>6. Referenzen</li>
				</ul>
			</mybody>
		</Layout>
		<Notes>
			These are some presenter notes that can help during the actual
			presentation.<br />
			They are displayed on the presenter's screen if "presenter mode" has been entered.
		</Notes>
	</Slide>

	<script>
		newChapter('Motivation')
	</script>
	<Slide>
		<Layout>
			<titlebar>Frage</titlebar>
			<mybody>
				<ul>
					<li>
						Wie viel CO₂-Emissionen werden geschätzt, dass das Training eines
						großen maschinellen Lernmodells wie GPT-3 verursacht?
					</li>
					<br />
					<li style="margin-bottom: 10px;">
						A) So viel wie ein Kühlschrank in einem Jahr
					</li>
					<li style="margin-bottom: 10px;">
						B) So viel wie ein Auto in einem Jahr
					</li>
					<li style="margin-bottom: 10px;">
						C) So viel wie fünf Autos in ihrem gesamten Lebenszyklus
					</li>
				</ul>
			</mybody>
		</Layout>
	</Slide>

	<Slide
		><Layout>
			<titlebar>ChatGPT Frage-Antwort</titlebar>
			<mybody>
				<ul>
					<li style="font-size: 0.6em;">
						Ich möchte mein Seminar mit einer Frage anfangen, kannst du mir
						bitte eine Frage bezüglich meiner Präsentation formulieren?
					</li>
					<br />
					<div class="flex-1 flex items-center justify-center flex-col">
						<!-- svelte-ignore a11y-missing-attribute -->
						<img class="h-[50vh] align-middle mb-2" src="ChatGPT-Frage.jpg" />
						<div class="text-xs mt-auto">Quelle: ChatGPT</div>
					</div>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<script>
		newChapter('ML')
	</script>
	<!--Definition ML-->
	<Slide>
		<Layout>
			<titlebar>Definition - ML</titlebar>
			<mybody>
				<div class="flex items-center justify-center">
					<div class="flex-1" style="padding-left: 20px; margin-right: 10px;">
						<br />
						<br />
						<p style="font-size: 0.6em;">
							"Maschinelles Lernen ist ein Teilbereich der künstlichen
							Intelligenz.
						</p>
						<p style="font-size: 0.6em;">
							Der Schwerpunkt liegt dabei auf dem Trainieren von Computern,
						</p>
						<p style="font-size: 0.6em;">
							um aus Daten und Erfahrungen zu lernen und sich stets zu
							verbessern – anstatt explizit dafür programmiert zu werden*"
						</p>
						<hr style="border-top: 1px solid #ccc; margin: 8px 0;" />
						<p style="font-size: 0.3em;">* sap.com</p>
					</div>
					<div class="flex-1 flex items-center justify-center flex-col">
						<!-- svelte-ignore a11y-missing-attribute -->
						<img
							class="h-[50vh] align-middle mb-2"
							src="machine_learning-iberdrola.com.jpg"
						/>
						<div class="text-xs mt-auto">Quelle: iberdrola.com</div>
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes>
	</Slide>
	
	<Slide><Layout>
		<titlebar>ML - overview</titlebar>
		<mybody>
			<div class="flex items-center justify-center flex-col">
				<!-- svelte-ignore a11y-missing-attribute -->
				<img
					class="h-[70vh] align-middle mb-2"
					src="Machine_Learning-Overview.jpg"
				/>
				<div class="text-xs mt-auto">Quelle: github:christophm</div>
			</div>
		</mybody>
	</Layout></Slide
>

	<Slide><Layout>
		<titlebar >ML</titlebar>
			<figure>
				<video controls class="w-[70%] mx-auto my-auto p-2">
					<source src="Deep-Learning-Illustration.mp4" type="video/mp4" />
				</video>
				<div class="text-xs mt-auto">Quelle: kaggle.com</div>
			</figure>
		</Layout></Slide>

	<Slide>
		<Layout>
			<titlebar> Anwendungen im Maschinellen Lernen </titlebar>
			<div
				class="grid mt-[5%] mx-[5f%]"
				style="grid-template-columns: 1fr 1fr;"
			>
				<!-- svelte-ignore a11y-missing-attribute -->
				<img src="Image-Processing-bigml.jpg" class="h-[45vh] object-cover" />
				<div
					class="absolute bottom-0 left-0 right-0 bg-black bg-opacity-50 text-white text-center py-2"
				>
					Bildverarbeitung
				</div>
				<!-- svelte-ignore a11y-missing-attribute -->
				<img
					src="Image-Processing-researchgate.jpg"
					class="h-[40vh] object-cover"
				/>
			</div>
		</Layout>
	</Slide>

	<Slide>
		<Layout>
			<titlebar> Anwendungen im Maschinellen Lernen </titlebar>
			<div class="grid mt-[7%] mx-[3%]" style="grid-template-columns: 1fr 1fr;">
				<!-- svelte-ignore a11y-missing-attribute -->
				<img
					src="Speech-Recognition-pylessons.jpg"
					class="h-[45vh] object-cover"
				/>
				<div
					class="absolute bottom-0 left-0 right-0 bg-black bg-opacity-50 text-white text-center py-2"
				>
					Sprachverarbeitung und -erkennung
				</div>
				<!-- svelte-ignore a11y-missing-attribute -->
				<img
					src="Speech-Recognition-Kardome.jpg"
					class="h-[45vh] object-cover"
				/>
			</div>
		</Layout>
	</Slide>

	<script>
		newChapter('RZ & EV')
	</script>
	<!--1. RZ & EV-->
	<Slide
		><Layout>
			<titlebar>RZ und Energieverbrauch</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px;">
						"Obwohl Rechenzentren keinen schwarzen Rauch ausstoßen oder fettige
						Zahnräder mahlen, sind sie nicht frei von Umweltauswirkungen*"
					</li>
					<br />
					<hr style="border-top: 1px solid #ccc; margin: 8px 0;" />
					<p style="font-size: 0.3em;">* lbl.gov</p>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<!--2. RZ & EV-->
	<Slide
		><Layout>
			<titlebar>RZ und Energieverbrauch</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px">
						"Obwohl Rechenzentren keinen schwarzen Rauch ausstoßen oder fettige
						Zahnräder mahlen, sind sie nicht frei von Umweltauswirkungen"
					</li>
					<br />
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen jährlich ca. 200 TWh.
					</li>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<!--3. RZ & EV-->
	<Slide
		><Layout>
			<titlebar>RZ und Energieverbrauch</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px;">
						"Obwohl Rechenzentren keinen schwarzen Rauch ausstoßen oder fettige
						Zahnräder mahlen, sind sie nicht frei von Umweltauswirkungen"
					</li>
					<br />
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen jährlich ca. 200 TWh.
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen zwei Prozent des globalen Strombedarfs
					</li>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<!--4. RZ & EV-->
	<Slide
		><Layout>
			<titlebar>RZ und Energieverbrauch</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px;">
						"Obwohl Rechenzentren keinen schwarzen Rauch ausstoßen oder fettige
						Zahnräder mahlen, sind sie nicht frei von Umweltauswirkungen"
					</li>
					<br />
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen jährlich ca. 200 TWh.
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen zwei Prozent des globalen Strombedarfs
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Das ist mehr als der nationale Energieverbrauch einiger Länder,
						z.B. Iran.
					</li>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	><!--5. RZ & EV-->
	<Slide
		><Layout>
			<titlebar>RZ und Energieverbrauch</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px;">
						"Obwohl Rechenzentren keinen schwarzen Rauch ausstoßen oder fettige
						Zahnräder mahlen, sind sie nicht frei von Umweltauswirkungen"
					</li>
					<br />
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen jährlich ca. 200 TWh.
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verbrauchen zwei Prozent des globalen Strombedarfs
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Das ist mehr als der nationale Energieverbrauch einiger Länder,
						z.B. Iran.
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Rechenzentren verursachen CO2-Emissionen, etwa 0,3 % der globalen
						Emissionen.
					</li>
				
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<!-- Agenda -->
	<Slide
		><Layout>
			<titlebar>Engergieverbrauch Prognose</titlebar>
			<mybody>
				<div class="flex items-center justify-center flex-col">
					<!-- svelte-ignore a11y-missing-attribute -->
					<img
						class="h-[70vh] align-middle mb-2"
						src="Energieverbrauchsprognose.jpg"
					/>
					<div class="text-xs mt-auto">Quelle: datacenters.lbl.gov</div>
				</div>
			</mybody>
		</Layout>
		<Notes>
			These are some presenter notes that can help during the actual
			presentation.<br />
			They are displayed on the presenter's screen if "presenter mode" has been entered.
		</Notes></Slide
	>

	<script>
		newChapter('EV & KI')
	</script>
	<!--1. EV & KI-->
	<Slide
		><Layout>
			<titlebar>Energieverbrauch in der KI</titlebar>
			<mybody>
				<div class="flex items-center justify-center">
					<div class="flex-1">
						<br />
						<br />
						<br />
						<p style="font-size: 1.2em;">"KI ist alles andere als grün*"</p>
						<br />
						<br />
						<br />
						<hr style="border-top: 1px solid #ccc; margin: 8px 0;" />
						<p style="font-size: 0.3em;">* spektrum.de</p>
					</div>
					<div class="flex-1 flex items-center justify-center flex-col">
						<!-- svelte-ignore a11y-missing-attribute -->
						<img
							class="h-[70vh] align-middle mb-2"
							src="energy-consumption.jpg"
						/>
						<div class="text-xs mt-auto">Quelle: wsj.com</div>
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<!--2. EV & KI-->
	<Slide
		><Layout>
			<titlebar>Energieverbrauch in der KI</titlebar>
			<mybody>
				<div class="flex items-center justify-center">
					<div class="flex-1">
						<ul>
							<li style="margin-bottom: 2px; font-size: 0.6em;">
								"KI ist alles andere als grün."
							</li>
							<br />
							<li style="margin-bottom: 10px; font-size: 0.6em;">
								• CO2-Emissionen von fünf Autos über ihren gesamten
								Lebenszyklus.
							</li>
							<li style="margin-bottom: 10px; font-size: 0.6em;">
								• KI benötigt im Vergleich zum menschlichen Gehirn deutlich mehr
								Energie.
							</li>
							<li style="margin-bottom: 10px; font-size: 0.6em;">
								• BERT kann CO2-Fußabdruck eines transamerikanischen Fluges
								erreichen.
							</li>
						</ul>
					</div>
					<div class="flex-1 flex items-center justify-center flex-col">
						<!-- svelte-ignore a11y-missing-attribute -->
						<img
							class="h-[70vh] align-middle mb-2"
							src="energy-consumption.jpg"
						/>
						<div class="text-xs mt-auto">Quelle: wsj.com</div>
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>


	<Slide><Layout>
		<titlebar></titlebar>
		<mybody>
			<div class="flex items-center justify-center flex-col">
				<!-- svelte-ignore a11y-missing-attribute -->
				<img
					class="h-[70vh] align-middle mb-2"
					src="Deep-Learning.jpg"
				/>
				<div class="text-xs mt-auto">Quelle: arxiv.org</div>
			</div>
		</mybody>
	</Layout>
	<Notes>
		These are some presenter notes that can help during the actual
		presentation.<br />
		They are displayed on the presenter's screen if "presenter mode" has been entered.
	</Notes></Slide
>

<script>
	newChapter('SV GPT')
</script>
<Slide><Layout>
	<titlebar>Stromverbrauch von GPT-Modellen</titlebar>
	<mybody>
		<div class="flex items-center justify-center flex-col">
			<!-- svelte-ignore a11y-missing-attribute -->
			<img
				class="h-[50vh] align-middle mb-2"
				src="GPT_Electricity_Consumption.jpg"
			/>
		</div>
	</mybody>
</Layout>
<Notes>
	These are some presenter notes that can help during the actual
	presentation.<br />
	They are displayed on the presenter's screen if "presenter mode" has been entered.
</Notes></Slide
>
<Slide><Layout>
	<titlebar>Stromverbrauch von GPT-Modellen</titlebar>
	<mybody>
		<div class="flex items-center justify-center flex-col">
			<!-- svelte-ignore a11y-missing-attribute -->
			<img
				class="h-[50vh] align-middle mb-2"
				src="GPT_Electricity_Consumption_American-House.jpg"
			/>
		</div>
	</mybody>
</Layout>
<Notes>
	These are some presenter notes that can help during the actual
	presentation.<br />
	They are displayed on the presenter's screen if "presenter mode" has been entered.
</Notes></Slide
>

<script>
	newChapter('Schlussfolgerung')
</script>
<Slide
		><Layout>
			<titlebar>Schlussfolgerung</titlebar>
			<mybody>
				<ul>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Die Entwicklung der GPT-Modelle zeigt eine signifikante <br/> Zunahme im Stromverbrauch mit jeder Generation
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Hoher Energiebedarf pro Modell
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Notwendigkeit für Effizienzsteigerung und Forschung
					</li>
					<li style="margin-bottom: 10px; font-size: 0.6em;">
						• Herausforderungen für Skalierung und Nachhaltigkeit
					</li>
				</ul>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>


	<Slide
		><Layout>
			<titlebar>Durchschnittlicher Wachstumsrate GPT-3 - GPT-3.5</titlebar>
			<mybody>
				<div class="flex items-center justify-center flex-col">
					<!-- svelte-ignore a11y-missing-attribute -->
					<img
						class="h-[50vh] align-middle mb-2"
						src="GPT_Electricity_Consumption_GPT3_And_GPT3.5.jpg"
					/>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<Slide
		><Layout>
			<titlebar>Durchschnittlicher Wachstumsrate GPT-4 - GPT-5</titlebar>
			<mybody>
				<div class="flex items-center justify-center flex-col">
					<!-- svelte-ignore a11y-missing-attribute -->
					<img
						class="h-[50vh] align-middle mb-2"
						src="GPT_Electricity_Consumption_GPT4_And_GPT5.jpg"
					/>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<Slide
		><Layout>
			<titlebar>Durchschnittlicher Wachstumsrate GPT-3 - GPT-5</titlebar>
			<mybody>
				<div class="flex items-center justify-center flex-col">
					<!-- svelte-ignore a11y-missing-attribute -->
					<img
						class="h-[50vh] align-middle mb-2"
						src="GPT_Electricity_Consumption_All_Modules.jpg"
					/>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<script>
		newChapter('Referenzen')
	</script>
	<Slide>
		<Layout>
			<mybody>
				<ul class="a" style="font-size: 25px;">
					<li>Yu, et al., (2022)</li>
					<li>wsj.com <a href="https://www.wsj.com/tech/ai/ai-energy-consumption-fc79d94f">, (2024)</a></li>
					<li>Ingenieur.de <a href="https://www.ingenieur.de/technik/fachbereiche/ittk/warum-rechenzentren-als-systemrelevant-eingestuft-werden-muessen/">, (2023)</a></li>
					<li>bigml.com <a href="https://blog.bigml.com/2021/11/22/introduction-to-image-processing/">, (2023)</a></li>
					<li>researchgate.net <a href="https://www.researchgate.net/figure/Image-pixel-generation-In-Digital-Image-Processing-the-digital-image-feature-extraction_fig1_283800375">, (2023)</a></li>
					<li>pylessons.com <a href="https://pylessons.com/speech-recognition">, (2023)</a></li>
					<li>kardome.com <a href="https://www.kardome.com/blog-posts/difference-speech-and-voice-recognition">, (2023)</a></li>
					<li>arxiv.org <a href="https://arxiv.org/pdf/1906.02243">, Energy and Policy Considerations for Deep Learning in NLP</a></li>
					<li>arxiv.org <a href="https://arxiv.org/pdf/2303.01980">, Towards energy-efficient Deep Learning</a></li>
					<li>medium.com <a href="https://www.springboard.com/blog/data-science/machine-learning-gpt-3-open-ai/">, Is the energy consumption of large language model is over-hyped</a></li>
					<li>forbes.com <a href="https://www.forbes.com/sites/arielcohen/2024/05/23/ai-is-pushing-the-world-towards-an-energy-crisis/">, Is the energy consumption of large language model is over-hyped</a></li>
					<li>theverge.com <a href="https://www.theverge.com/24066646/ai-electricity-energy-watts-generative-consumption">, Is the energy consumption of large language model is over-hyped</a></li>
				</ul>
			</mybody>
		</Layout>
		<Notes>
			These are some presenter notes that can help during the actual presentation.<br />
			They are displayed on the presenter's screen if "presenter mode" has been entered.
		</Notes>
	</Slide>
	

	<script>
		newChapter('Anhang')
	</script>
	<Slide
		><Layout>
			<titlebar>Rechenzentren</titlebar>
			<mybody>
				<div class="flex items-center justify-center">
					<div class="flex-1">
						<p style="font-size: 0.8em;">Definition</p>
						<br />
						<p style="font-size: 0.5em;">
							IT-Betriebsbereiche, aus denen heraus <br /> Dienste/Dienstleistungen
							für Dritte erbracht werden, sind immer als RZ zu betrachten. Dabei
							ist es unerheblich, ob diese Erbringung gegen Entgelt erfolgt oder
							nicht.*
						</p>
						<br />
						<hr style="border-top: 1px solid #ccc; margin: 8px 0;" />
						<p style="font-size: 0.3em;">* BSI</p>
					</div>
					<div class="flex-1 flex items-center justify-center flex-col">
						<img class="h-[50vh] align-middle mb-2" src="Rechenzentrum.jpg" />
						<div class="text-xs mt-auto">Quelle: ingenieur.de</div>
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<Slide
		><Layout>
			<titlebar>Rechenzentren</titlebar>
			<mybody>
				<div class="flex items-center justify-center">
					<div class="flex-1">
						<p style="font-size: 0.8em;">Definition</p>
						<br />
						<p style="font-size: 0.6em;">
							Gebäude zur Unterbringung und Betrieb von IT-Infrastruktur
						</p>
					</div>
					<div class="flex-1 flex items-center justify-center flex-col">
						<img class="h-[50vh] align-middle mb-2" src="Rechenzentrum.jpg" />
						<div class="text-xs mt-auto">Quelle: ingenieur.de</div>
					</div>
				</div>
			</mybody>
		</Layout>
		<Notes></Notes></Slide
	>

	<Slide>
		<Layout>
			<titlebar>Frage | Gedankenexperiment</titlebar>
			<mybody>
				<ul>
					<li>
						Wenn ihr euch aus Protest für den Umweltschutz irgendwo festkleben
						könntet, wo würde das sein?
					</li>
					<br />
					<li style="margin-bottom: 10px;">1. Auf der Autobahn</li>
					<li style="margin-bottom: 10px;">2. Am Flughafen</li>
					<li style="margin-bottom: 10px;">3. Vor einem KI-Unternehmen</li>
					<li style="margin-bottom: 10px;">4. Auf Zuggleise</li>
				</ul>
			</mybody>
		</Layout>
	</Slide>

	<!-- to mimic the latex template  -->
	<!-- to mimic the latex template  -->
	<!-- to mimic the latex template  -->
	<!-- to mimic the latex template  -->
	<!-- to mimic the latex template  -->
	<!-- to mimic the latex template  -->
	<script>
		const totalSlides = document.getElementsByTagName('pagenumber').length
		const totalChapters = chapterNames.length
		var temp
		for (let i = 0; i < totalSlides; i++) {
			// one section, one slide
			document
				.getElementsByTagName('section')
				[i].setAttribute('id', 'slide-' + (i + 1))
			// add author name
			document.getElementsByTagName('author')[i].innerText = authorshort
			// add title
			document.getElementsByTagName('mytitle')[i].innerHTML =
				'<a href="#slide-1">' + title + '</a>'
			// show slide number with total slide number
			document.getElementsByTagName('pagenumber')[i].innerHTML =
				i + 1 + '/' + totalSlides
		}
		for (let i = 0; i < totalSlides; i++) {
			for (let j = 0; j < totalChapters; j++) {
				// fill in chapter names
				temp = document.querySelectorAll('table.topbar')[i]
				temp.getElementsByTagName('tr')[0].innerHTML +=
					'<th data-chpcol="chpcol" style="font-weight:normal">' +
					chapterNames[j] +
					'</th>'
				// document.getElementsByTagName("test")[0].innerHTML="here!";
				// fill in dots
				let slidesInChapter = presentationData.filter(
					(item) => item.chapter == chapterNames[j]
				)
				let begin = slidesInChapter[0].pagenr
				let end = slidesInChapter[slidesInChapter.length - 1].pagenr
				let circles = toCircle(begin, end)
				temp.getElementsByTagName('tr')[1].innerHTML +=
					'<td>' + circles + '</td>'
			}
		}
		for (let i = 0; i < totalSlides; i++) {
			// first, find out if title page and toc exist
			let chapter0 = presentationData.filter(
				(item) => item.chapternr == 0
			).length
			if (i >= chapter0) {
				// then set corresponding circle to white
				let circle = document.getElementsByTagName('circle-' + (i + 1))[i]
				circle.style.background = 'white'
				circle.style.border = '0px'
				// also the chapter names
				let chapterNr = presentationData.filter(
					(item) => item.pagenr == i + 1
				)[0].chapternr
				temp =
					document.getElementsByTagName('th')[i * totalChapters + chapterNr - 1]
				if (temp.hasAttribute('data-chpcol')) {
					temp.style.color = 'white'
				}
			}
		}
		// circles: start, start+1, . . . , end are created
		function toCircle(begin, end) {
			let circles = ''
			for (let i = begin; i <= end; i++) {
				circles +=
					'<a href="#slide-' +
					i +
					'"><circle-' +
					i +
					' class="dot"> </circle-' +
					i +
					'> </a>'
			}
			return circles
		}
		// to create table of contents
		if (toc) {
			for (i = 1; i <= chapterNames.length; i++) {
				document.getElementsByTagName('chpicons')[0].innerHTML +=
					'<div class="chpicon">' + i + '</div> <br>'
				document.getElementsByTagName('chpnames')[0].innerHTML +=
					'<div>' + chapterNames[i - 1] + '</div> <br>'
			}
		}
	</script>

	<style>
		.chpicon {
			color: white;
			width: 180%;
			background: var(--themecolor);
		}
		.dot {
			height: 15px;
			width: 15px;
			background: rgba(0, 0, 0, 0);
			border-radius: 50%;
			border: 1.5px solid var(--themecolorlight);
			display: inline-block;
		}
		ul.a {
			list-style-type: square;
			padding-top: 5vh;
		}
		ul.b {
			list-style-type: circle;
			margin-left: 5vh;
			margin-right: 5vh;
			padding-top: 1vh;
			padding-bottom: 1vh;
		}
		ul.c {
			list-style-type: disc;
			margin-left: 10vh;
			margin-right: 5vh;
			padding-top: 1vh;
			padding-bottom: 1vh;
		}
		ul {
			text-align: left;
			margin-left: 20vh;
			margin-right: 5vh;
			padding-top: 1vh;
			padding-bottom: 1vh;
		}
		titlebar {
			display: flex;
			background: rgb(242, 242, 242);
			width: 100vw;
			height: 9vh;
			text-align: left;
			padding-left: 5vh;
			padding-top: 2vh;
			font-size: 5vh;
		}
		mybody {
			display: flex;
			justify-content: center;
			align-items: center;
			height: 79vh;
		}
		figure {
			border: 0px #cccccc solid;
			padding: 4px;
			margin: auto;
		}
		figcaption {
			background-color: rgb(242, 242, 242);
			color: black;
			font-style: italic;
			padding: 2px;
			text-align: center;
		}
	</style>
</Presentation>
