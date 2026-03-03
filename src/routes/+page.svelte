<script>
	import {
		Menu,
		X,
		Zap,
		ChevronRight,
		Users,
		BarChart3,
		Shield,
		Cpu,
		Globe,
		Trophy,
		UserPlus,
		TrendingUp,
		Target,
		Eye,
		Heart,
		Check,
		ArrowUp,
		ArrowDown
	} from '@lucide/svelte';
	import { resolve } from '$app/paths';
	let mobileOpen = false;

	const navLinks = [
		{ href: '#about', label: 'O que somos' },
		{ href: '#how-it-works', label: 'Como funciona' },
		{ href: '#scoring', label: 'Pontuação' },
		{ href: '#plans', label: 'Planos' }
	];

	const features = [
		{
			icon: Shield,
			title: 'Dados Oficiais',
			description: 'Integração direta com APIs que fornecem estatísticas oficiais do Brasileirão.'
		},
		{
			icon: Cpu,
			title: 'Processamento Ágil',
			description: 'Cálculo de pontuação em tempo real assim que os dados são validados.'
		},
		{
			icon: Globe,
			title: 'Acesso Global',
			description: 'Plataforma otimizada para web e dispositivos móveis, jogue de onde estiver.'
		},
		{
			icon: Trophy,
			title: 'Competitividade',
			description: 'Sistema de ligas e rankings que estimula a interação entre os usuários.'
		}
	];

	const steps = [
		{
			icon: UserPlus,
			number: '01',
			title: 'Crie sua conta',
			description: 'Faça seu cadastro gratuito na DraftFut em poucos segundos.'
		},
		{
			icon: Users,
			number: '02',
			title: 'Monte seu time',
			description:
				'Escolha jogadores reais do Campeonato Brasileiro para compor o seu time virtual.'
		},
		{
			icon: BarChart3,
			number: '03',
			title: 'Dados em tempo real',
			description: 'A cada rodada, o sistema coleta automaticamente os dados oficiais das partidas.'
		},
		{
			icon: Trophy,
			number: '04',
			title: 'Pontuação automática',
			description: 'A pontuação é calculada com base no desempenho real dos atletas em campo.'
		},
		{
			icon: TrendingUp,
			number: '05',
			title: 'Dispute e evolua',
			description:
				'Participe de ligas, dispute rankings e acompanhe sua evolução ao longo da temporada.'
		}
	];

	const positiveScoring = [
		{ action: 'Gol marcado', points: '+8' },
		{ action: 'Assistência', points: '+5' },
		{ action: 'Pênalti defendido', points: '+7' },
		{ action: 'Jogo sem sofrer gol', points: '+5' },
		{ action: 'Defesa difícil (goleiro)', points: '+3' },
		{ action: 'Desarme', points: '+1,5' },
		{ action: 'Finalização no gol', points: '+1' }
	];

	const negativeScoring = [
		{ action: 'Gol contra', points: '-6' },
		{ action: 'Cartão vermelho', points: '-5' },
		{ action: 'Pênalti perdido', points: '-4' },
		{ action: 'Cartão amarelo', points: '-2' },
		{ action: 'Gol sofrido (goleiro)', points: '-1' }
	];

	const plans = [
		{
			name: 'Free',
			price: 'R$ 0',
			description: 'Para quem está começando no mundo do fantasy game.',
			features: [
				'Participação em 1 liga pública',
				'Escalação padrão',
				'Estatísticas básicas',
				'Ranking geral'
			],
			cta: 'Começar Agora',
			highlighted: false
		},
		{
			name: 'Pro',
			price: 'R$ 19,90',
			period: '/mês',
			description: 'Para o torcedor que quer levar a competição a sério.',
			features: [
				'Ligas públicas ilimitadas',
				'Criação de 5 ligas privadas',
				'Estatísticas avançadas',
				'Dicas de especialistas',
				'Sem anúncios'
			],
			cta: 'Assinar Pro',
			highlighted: true
		},
		{
			name: 'Elite',
			price: 'R$ 39,90',
			period: '/mês',
			description: 'A experiência completa para os mestres da estratégia.',
			features: [
				'Tudo do plano Pro',
				'Ligas privadas ilimitadas',
				'Análise preditiva de jogadores',
				'Prêmios exclusivos por rodada',
				'Suporte prioritário'
			],
			cta: 'Seja Elite',
			highlighted: false
		}
	];

	const values = [
		{ icon: Shield, label: 'Transparência' },
		{ icon: Cpu, label: 'Inovação' },
		{ icon: Users, label: 'Comunidade' },
		{ icon: Target, label: 'Precisão' }
	];

	let currentYear = new Date().getFullYear();
</script>

<svelte:head>
	<title>DraftFut | Fantasy Game do Futebol Brasileiro</title>
	<meta
		name="description"
		content="Monte seu time virtual, acompanhe estatísticas em tempo real e dispute rankings no fantasy game oficial do Campeonato Brasileiro."
	/>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
	<link
		href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Oswald:wght@400;500;600;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="bg-background text-foreground min-h-screen font-sans antialiased">
	<!-- Navbar -->
	<header
		class="border-border/50 bg-background/80 fixed top-0 z-50 w-full border-b backdrop-blur-xl"
	>
		<nav class="mx-auto flex max-w-7xl items-center justify-between px-6 py-4">
			<a href="#top" class="flex items-center gap-2">
				<div class="bg-primary flex h-8 w-8 items-center justify-center rounded-lg">
					<span class="font-heading text-primary-foreground text-sm font-bold">D</span>
				</div>
				<span class="font-heading text-foreground text-xl font-bold tracking-tight">
					DRAFTFUT
				</span>
			</a>
			<div class="hidden items-center gap-8 md:flex">
				{#each navLinks as link (link)}
					<a
						href={resolve(link.href)}
						class="text-muted-foreground hover:text-foreground text-sm transition-colors"
					>
						{link.label}
					</a>
				{/each}
			</div>
			<div class="hidden md:block">
				<button
					class="bg-primary text-primary-foreground hover:bg-primary/90 inline-flex h-9 items-center justify-center rounded-md px-4 py-2 text-sm font-medium transition-all"
				>
					Comece Grátis
				</button>
			</div>
			<button
				on:click={() => (mobileOpen = !mobileOpen)}
				class="text-foreground md:hidden"
				aria-label={mobileOpen ? 'Fechar menu' : 'Abrir menu'}
			>
				{#if mobileOpen}
					<X class="h-6 w-6" />
				{:else}
					<Menu class="h-6 w-6" />
				{/if}
			</button>
		</nav>
		{#if mobileOpen}
			<div class="border-border/50 bg-background/95 border-t backdrop-blur-xl md:hidden">
				<div class="flex flex-col gap-4 px-6 py-6">
					{#each navLinks as link (link.href)}
						<a
							href={resolve(link.href)}
							on:click={() => (mobileOpen = false)}
							class="text-muted-foreground hover:text-foreground text-base transition-colors"
						>
							{link.label}
						</a>
					{/each}
					<button
						class="bg-primary text-primary-foreground hover:bg-primary/90 mt-2 inline-flex h-9 w-full items-center justify-center rounded-md px-4 py-2 text-sm font-medium transition-all"
					>
						Comece Grátis
					</button>
				</div>
			</div>
		{/if}
	</header>

	<main>
		<!-- Hero Section -->
		<section class="relative min-h-screen overflow-hidden">
			<div class="absolute inset-0">
				<img
					src="/images/hero-stadium.jpg"
					alt="Estádio de futebol iluminado"
					class="h-full w-full object-cover opacity-40"
				/>
				<div
					class="from-background/70 via-background/80 to-background absolute inset-0 bg-gradient-to-b"
				></div>
				<div
					class="from-background/90 via-background/40 absolute inset-0 bg-gradient-to-r to-transparent"
				></div>
			</div>
			<div
				class="relative mx-auto flex max-w-7xl flex-col items-start justify-center gap-8 px-6 pt-32 pb-24 md:min-h-screen md:pt-40"
			>
				<div
					class="border-primary/30 bg-primary/10 inline-flex items-center gap-2 rounded-full border px-4 py-1.5"
				>
					<Zap class="text-primary h-4 w-4" />
					<span class="text-primary text-sm font-medium">Fantasy Game do Brasileirão</span>
				</div>
				<h1
					class="font-heading text-foreground max-w-3xl text-5xl leading-tight font-bold tracking-tight md:text-7xl lg:text-8xl"
				>
					<span class="text-balance">SUA PAIXÃO, SUA ESTRATÉGIA</span>
				</h1>
				<p class="text-muted-foreground max-w-xl text-lg leading-relaxed md:text-xl">
					Monte seu time virtual com jogadores reais do Campeonato Brasileiro. Acompanhe
					estatísticas em tempo real e dispute rankings com seus amigos.
				</p>
				<div class="flex flex-col gap-4 sm:flex-row">
					<button
						class="bg-primary text-primary-foreground hover:bg-primary/90 inline-flex h-12 items-center justify-center gap-2 rounded-md px-10 text-lg font-semibold transition-all"
					>
						Criar Minha Conta
						<ChevronRight class="h-5 w-5" />
					</button>
					<button
						class="border-border text-foreground hover:bg-secondary inline-flex h-12 items-center justify-center gap-2 rounded-md border px-8 text-lg font-medium transition-all"
					>
						Saiba Mais
					</button>
				</div>
				<div class="mt-8 grid grid-cols-1 gap-6 sm:grid-cols-3">
					{#each [{ icon: Users, label: 'Ligas públicas e privadas', value: 'Compete' }, { icon: BarChart3, label: 'Dados oficiais em tempo real', value: 'Analise' }, { icon: Zap, label: 'Pontuação automática', value: 'Acompanhe' }] as item (item.icon)}
						<div
							class="border-border/50 bg-card/50 flex items-center gap-4 rounded-xl border px-5 py-4 backdrop-blur-sm"
						>
							<div
								class="bg-primary/10 flex h-10 w-10 shrink-0 items-center justify-center rounded-lg"
							>
								<svelte:component this={item.icon} class="text-primary h-5 w-5" />
							</div>
							<div>
								<p class="text-foreground text-sm font-bold">{item.value}</p>
								<p class="text-muted-foreground text-xs">{item.label}</p>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</section>

		<!-- About Section -->
		<section id="about" class="py-24 md:py-32">
			<div class="mx-auto max-w-7xl px-6">
				<div class="grid grid-cols-1 items-center gap-16 lg:grid-cols-2">
					<div>
						<span class="text-primary text-sm font-semibold tracking-widest uppercase">
							O que somos
						</span>
						<h2
							class="font-heading text-foreground mt-4 text-4xl font-bold tracking-tight md:text-5xl"
						>
							<span class="text-balance">TECNOLOGIA E FUTEBOL EM UMA SÓ PLATAFORMA</span>
						</h2>
						<p class="text-muted-foreground mt-6 text-lg leading-relaxed">
							A DraftFut é uma empresa focada no desenvolvimento de soluções digitais voltadas ao
							fantasy game esportivo. Utilizamos integração com APIs oficiais para coletar dados
							reais das partidas do Campeonato Brasileiro, garantindo informações confiáveis e
							atualizadas.
						</p>
						<p class="text-muted-foreground mt-4 text-lg leading-relaxed">
							Atuamos no segmento de tecnologia e entretenimento digital, conectando torcedores ao
							futebol de forma estratégica e dinâmica.
						</p>
					</div>
					<div class="grid grid-cols-1 gap-4 sm:grid-cols-2">
						{#each features as feature (feature)}
							<div
								class="group border-border/50 bg-card hover:border-primary/30 hover:bg-card/80 rounded-2xl border p-6 transition-all"
							>
								<div
									class="bg-primary/10 group-hover:bg-primary/20 mb-4 flex h-12 w-12 items-center justify-center rounded-xl transition-colors"
								>
									<svelte:component this={feature.icon} class="text-primary h-6 w-6" />
								</div>
								<h3 class="text-foreground mb-2 text-lg font-bold">{feature.title}</h3>
								<p class="text-muted-foreground text-sm leading-relaxed">
									{feature.description}
								</p>
							</div>
						{/each}
					</div>
				</div>
			</div>
		</section>

		<!-- How It Works Section -->
		<section id="how-it-works" class="relative py-24 md:py-32">
			<div
				class="via-primary/[0.02] absolute inset-0 bg-gradient-to-b from-transparent to-transparent"
			/>
			<div class="relative mx-auto max-w-7xl px-6">
				<div class="text-center">
					<span class="text-primary text-sm font-semibold tracking-widest uppercase">
						Como funciona
					</span>
					<h2
						class="font-heading text-foreground mt-4 text-4xl font-bold tracking-tight md:text-5xl"
					>
						<span class="text-balance">DO CAMPO PARA SUA TELA</span>
					</h2>
					<p class="text-muted-foreground mx-auto mt-6 max-w-2xl text-lg leading-relaxed">
						Em cinco passos simples, você transforma sua paixão pelo futebol em uma experiência
						estratégica e competitiva.
					</p>
				</div>
				<div class="mt-16 grid grid-cols-1 gap-8 md:grid-cols-5">
					{#each steps as step, index (step)}
						<div class="group relative text-center">
							{#if index < steps.length - 1}
								<div
									class="from-primary/30 absolute top-10 right-0 hidden h-0.5 w-full translate-x-1/2 bg-gradient-to-r to-transparent md:block"
								/>
							{/if}
							<div
								class="border-border/50 bg-card group-hover:border-primary/50 group-hover:bg-primary/10 relative mx-auto mb-6 flex h-20 w-20 items-center justify-center rounded-2xl border transition-all"
							>
								<svelte:component this={step.icon} class="text-primary h-8 w-8" />
								<span
									class="bg-primary text-primary-foreground absolute -top-2 -right-2 flex h-6 w-6 items-center justify-center rounded-full text-xs font-bold"
								>
									{step.number}
								</span>
							</div>
							<h3 class="text-foreground mb-2 text-lg font-bold">{step.title}</h3>
							<p class="text-muted-foreground text-sm leading-relaxed">{step.description}</p>
						</div>
					{/each}
				</div>
			</div>
		</section>

		<!-- Scoring Section -->
		<section id="scoring" class="py-24 md:py-32">
			<div class="mx-auto max-w-7xl px-6">
				<div class="text-center">
					<span class="text-primary text-sm font-semibold tracking-widest uppercase">
						Sistema de pontuação
					</span>
					<h2
						class="font-heading text-foreground mt-4 text-4xl font-bold tracking-tight md:text-5xl"
					>
						<span class="text-balance">DESEMPENHO REAL, PONTUAÇÃO JUSTA</span>
					</h2>
					<p class="text-muted-foreground mx-auto mt-6 max-w-2xl text-lg leading-relaxed">
						A pontuação é baseada no desempenho real dos jogadores em campo. Atualização automática
						após cada rodada, garantindo transparência e competitividade.
					</p>
				</div>
				<div class="mt-16 grid grid-cols-1 gap-8 md:grid-cols-2">
					<div class="border-primary/20 bg-card rounded-2xl border p-8">
						<div class="mb-6 flex items-center gap-3">
							<div class="bg-primary/10 flex h-10 w-10 items-center justify-center rounded-lg">
								<ArrowUp class="text-primary h-5 w-5" />
							</div>
							<h3 class="text-foreground text-xl font-bold">Pontuação Positiva</h3>
						</div>
						<div class="flex flex-col gap-3">
							{#each positiveScoring as item (item)}
								<div
									class="border-border/30 bg-secondary/30 flex items-center justify-between rounded-xl border px-5 py-3"
								>
									<span class="text-foreground text-sm">{item.action}</span>
									<span class="font-heading text-primary text-lg font-bold">
										{item.points}
									</span>
								</div>
							{/each}
						</div>
					</div>
					<div class="border-destructive/20 bg-card rounded-2xl border p-8">
						<div class="mb-6 flex items-center gap-3">
							<div class="bg-destructive/10 flex h-10 w-10 items-center justify-center rounded-lg">
								<ArrowDown class="text-destructive h-5 w-5" />
							</div>
							<h3 class="text-foreground text-xl font-bold">Pontuação Negativa</h3>
						</div>
						<div class="flex flex-col gap-3">
							{#each negativeScoring as item (item)}
								<div
									class="border-border/30 bg-secondary/30 flex items-center justify-between rounded-xl border px-5 py-3"
								>
									<span class="text-foreground text-sm">{item.action}</span>
									<span class="font-heading text-destructive text-lg font-bold">
										{item.points}
									</span>
								</div>
							{/each}
						</div>
					</div>
				</div>
			</div>
		</section>

		<!-- Plans Section -->
		<section id="plans" class="py-24 md:py-32">
			<div class="mx-auto max-w-7xl px-6">
				<div class="text-center">
					<span class="text-primary text-sm font-semibold tracking-widest uppercase">
						Planos e preços
					</span>
					<h2
						class="font-heading text-foreground mt-4 text-4xl font-bold tracking-tight md:text-5xl"
					>
						<span class="text-balance">ESCOLHA SUA ESTRATÉGIA</span>
					</h2>
					<p class="text-muted-foreground mx-auto mt-6 max-w-2xl text-lg leading-relaxed">
						Temos o plano ideal para cada tipo de jogador, do iniciante ao profissional.
					</p>
				</div>
				<div class="mt-16 grid grid-cols-1 gap-8 md:grid-cols-3">
					{#each plans as plan (plan.cta)}
						<div
							class={`relative flex flex-col rounded-3xl border p-8 transition-all hover:scale-[1.02] ${
								plan.highlighted
									? 'border-primary bg-card shadow-primary/10 shadow-2xl'
									: 'border-border/50 bg-card/50'
							}`}
						>
							{#if plan.highlighted}
								<div
									class="bg-primary text-primary-foreground absolute -top-4 left-1/2 -translate-x-1/2 rounded-full px-4 py-1 text-xs font-bold"
								>
									MAIS POPULAR
								</div>
							{/if}
							<div class="mb-8">
								<h3 class="text-foreground text-xl font-bold">{plan.name}</h3>
								<div class="mt-4 flex items-baseline gap-1">
									<span class="font-heading text-foreground text-4xl font-bold">{plan.price}</span>
									{#if plan.period}
										<span class="text-muted-foreground text-sm">{plan.period}</span>
									{/if}
								</div>
								<p class="text-muted-foreground mt-4 text-sm">{plan.description}</p>
							</div>
							<ul class="flex-1 space-y-4">
								{#each plan.features as feature (feature)}
									<li class="flex items-center gap-3">
										<div
											class={`flex h-5 w-5 items-center justify-center rounded-full ${
												plan.highlighted ? 'bg-primary/20' : 'bg-secondary'
											}`}
										>
											<Check
												class={`h-3 w-3 ${
													plan.highlighted ? 'text-primary' : 'text-muted-foreground'
												}`}
											/>
										</div>
										<span class="text-foreground text-sm">{feature}</span>
									</li>
								{/each}
							</ul>
							<button
								class={`mt-8 inline-flex h-11 w-full items-center justify-center rounded-md px-8 text-base font-semibold transition-all ${
									plan.highlighted
										? 'bg-primary text-primary-foreground hover:bg-primary/90'
										: 'bg-secondary text-secondary-foreground hover:bg-secondary/80'
								}`}
							>
								{plan.cta}
							</button>
						</div>
					{/each}
				</div>
			</div>
		</section>

		<!-- Mission Section -->
		<section class="py-24 md:py-32">
			<div class="mx-auto max-w-7xl px-6">
				<div class="grid grid-cols-1 gap-8 md:grid-cols-3">
					<div class="border-border/50 bg-card rounded-2xl border p-8">
						<div class="bg-primary/10 mb-6 flex h-12 w-12 items-center justify-center rounded-xl">
							<Target class="text-primary h-6 w-6" />
						</div>
						<h3 class="font-heading text-foreground text-2xl font-bold">MISSÃO</h3>
						<p class="text-muted-foreground mt-4 text-base leading-relaxed">
							Proporcionar uma experiência inovadora no fantasy game esportivo, conectando dados
							reais do futebol com estratégia, tecnologia e competição.
						</p>
					</div>
					<div class="border-primary/30 bg-card rounded-2xl border p-8">
						<div class="bg-primary/10 mb-6 flex h-12 w-12 items-center justify-center rounded-xl">
							<Eye class="text-primary h-6 w-6" />
						</div>
						<h3 class="font-heading text-foreground text-2xl font-bold">VISÃO</h3>
						<p class="text-muted-foreground mt-4 text-base leading-relaxed">
							Tornar-se referência nacional em fantasy games baseados no futebol brasileiro,
							destacando-se pela inovação, confiabilidade e experiência do usuário.
						</p>
					</div>
					<div class="border-border/50 bg-card rounded-2xl border p-8">
						<div class="bg-primary/10 mb-6 flex h-12 w-12 items-center justify-center rounded-xl">
							<Heart class="text-primary h-6 w-6" />
						</div>
						<h3 class="font-heading text-foreground text-2xl font-bold">VALORES</h3>
						<div class="mt-4 flex flex-wrap gap-2">
							{#each values as value (value)}
								<span
									class="border-border/50 bg-secondary/50 text-foreground inline-flex items-center gap-1.5 rounded-full border px-3 py-1.5 text-xs"
								>
									<svelte:component this={value.icon} class="text-primary h-3 w-3" />
									{value.label}
								</span>
							{/each}
						</div>
					</div>
				</div>
			</div>
		</section>

		<!-- CTA Section -->
		<section class="relative py-24 md:py-32">
			<div
				class="from-primary/5 absolute inset-0 bg-gradient-to-t via-transparent to-transparent"
			/>
			<div class="relative mx-auto max-w-4xl px-6 text-center">
				<h2 class="font-heading text-foreground text-4xl font-bold tracking-tight md:text-6xl">
					<span class="text-balance">PRONTO PARA ESCALAR SEU TIME?</span>
				</h2>
				<p class="text-muted-foreground mx-auto mt-6 max-w-xl text-lg leading-relaxed">
					Cadastre-se agora, monte seu time virtual e mostre que você entende de futebol como
					ninguém. É grátis!
				</p>
				<div class="mt-10 flex flex-col items-center justify-center gap-4 sm:flex-row">
					<button
						class="bg-primary text-primary-foreground hover:bg-primary/90 inline-flex h-12 items-center justify-center gap-2 rounded-md px-10 text-lg font-semibold transition-all"
					>
						Criar Minha Conta
						<ChevronRight class="h-5 w-5" />
					</button>
				</div>
			</div>
		</section>
	</main>

	<!-- Footer -->
	<footer class="border-border/50 border-t py-12">
		<div class="mx-auto max-w-7xl px-6">
			<div class="flex flex-col items-center justify-between gap-6 md:flex-row">
				<div class="flex items-center gap-2">
					<div class="bg-primary flex h-8 w-8 items-center justify-center rounded-lg">
						<span class="font-heading text-primary-foreground text-sm font-bold"> D </span>
					</div>
					<span class="font-heading text-foreground text-lg font-bold tracking-tight">
						DRAFTFUT
					</span>
				</div>
				<div class="flex flex-wrap items-center justify-center gap-6">
					{#each navLinks as link (link.href)}
						<a
							href={resolve(link.href)}
							class="text-muted-foreground hover:text-foreground text-sm transition-colors"
						>
							{link.label}
						</a>
					{/each}
				</div>
				<p class="text-muted-foreground text-sm">
					&copy; {currentYear} DraftFut. Todos os direitos reservados.
				</p>
			</div>
		</div>
	</footer>
</div>

<style>
	:global(:root) {
		--background: oklch(0.1 0.005 240);
		--foreground: oklch(0.97 0 0);
		--card: oklch(0.15 0.005 240);
		--card-foreground: oklch(0.97 0 0);
		--popover: oklch(0.15 0.005 240);
		--popover-foreground: oklch(0.97 0 0);
		--primary: oklch(0.72 0.19 145);
		--primary-foreground: oklch(0.1 0.02 145);
		--secondary: oklch(0.2 0.005 240);
		--secondary-foreground: oklch(0.92 0 0);
		--muted: oklch(0.2 0.005 240);
		--muted-foreground: oklch(0.65 0 0);
		--accent: oklch(0.72 0.19 145);
		--accent-foreground: oklch(0.1 0.02 145);
		--destructive: oklch(0.577 0.245 27.325);
		--destructive-foreground: oklch(0.577 0.245 27.325);
		--border: oklch(0.25 0.005 240);
		--input: oklch(0.25 0.005 240);
		--ring: oklch(0.72 0.19 145);
		--radius: 0.625rem;
	}

	.font-sans {
		font-family: 'Inter', sans-serif;
	}

	.font-heading {
		font-family: 'Oswald', sans-serif;
	}

	/* Tailwind-like utility classes for colors using CSS variables */
	.bg-background {
		background-color: var(--background);
	}
	.text-foreground {
		color: var(--foreground);
	}
	.bg-card {
		background-color: var(--card);
	}
	.bg-primary {
		background-color: var(--primary);
	}
	.text-primary {
		color: var(--primary);
	}
	.text-primary-foreground {
		color: var(--primary-foreground);
	}
	.bg-secondary {
		background-color: var(--secondary);
	}
	.text-secondary-foreground {
		color: var(--secondary-foreground);
	}
	.text-muted-foreground {
		color: var(--muted-foreground);
	}
	.border-border {
		border-color: var(--border);
	}
	.border-primary {
		border-color: var(--primary);
	}
	.bg-destructive {
		background-color: var(--destructive);
	}
	.text-destructive {
		color: var(--destructive);
	}

	/* Custom gradients and effects */
	.bg-primary\/10 {
		background-color: color-mix(in srgb, var(--primary), transparent 90%);
	}
	.bg-primary\/20 {
		background-color: color-mix(in srgb, var(--primary), transparent 80%);
	}
	.bg-primary\/5 {
		background-color: color-mix(in srgb, var(--primary), transparent 95%);
	}
	.bg-secondary\/30 {
		background-color: color-mix(in srgb, var(--secondary), transparent 70%);
	}
	.bg-secondary\/50 {
		background-color: color-mix(in srgb, var(--secondary), transparent 50%);
	}
	.bg-card\/50 {
		background-color: color-mix(in srgb, var(--card), transparent 50%);
	}
	.bg-card\/80 {
		background-color: color-mix(in srgb, var(--card), transparent 20%);
	}
	.bg-destructive\/10 {
		background-color: color-mix(in srgb, var(--destructive), transparent 90%);
	}
	.border-primary\/30 {
		border-color: color-mix(in srgb, var(--primary), transparent 70%);
	}
	.border-primary\/20 {
		border-color: color-mix(in srgb, var(--primary), transparent 80%);
	}
	.border-primary\/50 {
		border-color: color-mix(in srgb, var(--primary), transparent 50%);
	}
	.border-border\/50 {
		border-color: color-mix(in srgb, var(--border), transparent 50%);
	}
	.border-border\/30 {
		border-color: color-mix(in srgb, var(--border), transparent 70%);
	}
	.border-destructive\/20 {
		border-color: color-mix(in srgb, var(--destructive), transparent 80%);
	}
	.shadow-primary\/10 {
		--tw-shadow-color: color-mix(in srgb, var(--primary), transparent 90%);
	}
</style>
