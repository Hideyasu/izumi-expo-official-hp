<script>
	import { onMount } from 'svelte';

	let scrollY = 0;
	let innerHeight = 0;

	onMount(() => {
		const handleScroll = () => scrollY = window.scrollY;
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function handleImageError(event) {
		const img = event.target;
		const parent = img.parentElement;

		// 画像を非表示にして、プレースホルダーを表示
		img.style.display = 'none';

		// プレースホルダーが既に存在する場合は何もしない
		if (parent.querySelector('.image-placeholder')) return;

		// プレースホルダー要素を作成
		const placeholder = document.createElement('div');
		placeholder.className = 'image-placeholder flex flex-col items-center justify-center w-full h-full text-gray-400';
		placeholder.innerHTML = `
			<svg class="w-12 h-12 mb-2" fill="none" stroke="currentColor" viewBox="0 0 24 24">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z"></path>
			</svg>
			<span class="text-xs">画像準備中</span>
		`;
		parent.appendChild(placeholder);
	}
</script>

<svelte:window bind:scrollY bind:innerHeight />

<!-- ヒーローセクション -->
<section class="relative min-h-screen bg-gradient-to-br from-blue-900 via-blue-700 to-blue-500 overflow-hidden">
	<!-- 背景装飾 -->
	<div class="absolute inset-0">
		<div class="absolute top-1/4 left-1/4 w-64 h-64 bg-white/10 rounded-full blur-3xl transform -translate-x-1/2 -translate-y-1/2"></div>
		<div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-white/5 rounded-full blur-3xl"></div>
	</div>
	
	<!-- ナビゲーション -->
	<nav class="relative z-10 px-6 py-6">
		<div class="max-w-7xl mx-auto flex justify-between items-center">
			<div class="text-white font-bold text-xl">いずみ万博 2025</div>
			<div class="hidden md:flex space-x-8 text-white">
				<a href="#about" class="hover:text-blue-200 transition-colors">概要</a>
				<a href="#events" class="hover:text-blue-200 transition-colors">イベント</a>
				<a href="#pavilions" class="hover:text-blue-200 transition-colors">パビリオン</a>
				<a href="#access" class="hover:text-blue-200 transition-colors">アクセス</a>
				<a href="#contact" class="hover:text-blue-200 transition-colors">お問い合わせ</a>
			</div>
		</div>
	</nav>
	
	<!-- メインビジュアル -->
	<div class="relative z-10 flex items-center justify-center min-h-[80vh] px-6">
		<div class="text-center text-white">
			<h1 class="text-5xl md:text-7xl font-bold mb-6 leading-tight">
				いのち輝く<br>
				<span class="text-blue-200">未来社会のいずみ</span>
			</h1>
			<p class="text-xl md:text-2xl mb-8 opacity-90">
				和泉市制施行70周年記念
			</p>
			<div class="text-lg md:text-xl mb-12 space-y-2">
				<p class="font-semibold">2025年10月25日（土）10:00〜19:00</p>
				<p>エコールいずみ・桃山学院大学・久保惣記念美術館</p>
			</div>
			<div class="flex flex-col sm:flex-row gap-4 justify-center">
				<a href="#about" class="bg-white text-blue-900 px-8 py-4 rounded-full font-semibold hover:bg-blue-50 transition-colors">
					詳細を見る
				</a>
				<a href="#contact" class="border-2 border-white text-white px-8 py-4 rounded-full font-semibold hover:bg-white hover:text-blue-900 transition-colors">
					お問い合わせ
				</a>
			</div>
		</div>
	</div>
</section>

<!-- 概要セクション -->
<section id="about" class="py-20 bg-white">
	<div class="max-w-7xl mx-auto px-6">
		<div class="text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">いずみ万博とは</h2>
			<p class="text-xl text-gray-600 max-w-3xl mx-auto">
				和泉市の市制施行70周年を記念し、市の未来社会を探求するイベントです。<br>
				伝統文化、テクノロジー、コミュニティの繋がりを促進し、多世代・多業種の交流を目指します。
			</p>
		</div>
		
		<div class="grid md:grid-cols-3 gap-8">
			<div class="text-center p-8 bg-blue-50 rounded-2xl">
				<div class="w-16 h-16 bg-blue-500 rounded-full mx-auto mb-6 flex items-center justify-center">
					<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"></path>
					</svg>
				</div>
				<h3 class="text-2xl font-bold text-gray-900 mb-4">伝統・文化</h3>
				<p class="text-gray-600">久保惣記念美術館、さをり織り、いずみ木綿など、和泉市の豊かな伝統文化を体験</p>
			</div>
			
			<div class="text-center p-8 bg-green-50 rounded-2xl">
				<div class="w-16 h-16 bg-green-500 rounded-full mx-auto mb-6 flex items-center justify-center">
					<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.75 17L9 20l-1 1h8l-1-1-.75-3M3 13h18M5 17h14a2 2 0 002-2V5a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
					</svg>
				</div>
				<h3 class="text-2xl font-bold text-gray-900 mb-4">テクノロジー</h3>
				<p class="text-gray-600">いずみを中心とした最新技術の展示・体験</p>
			</div>
			
			<div class="text-center p-8 bg-purple-50 rounded-2xl">
				<div class="w-16 h-16 bg-purple-500 rounded-full mx-auto mb-6 flex items-center justify-center">
					<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"></path>
					</svg>
				</div>
				<h3 class="text-2xl font-bold text-gray-900 mb-4">コミュニティ</h3>
				<p class="text-gray-600">多世代・多業種の交流を通じて、地域コミュニティの絆を深める</p>
			</div>
		</div>
	</div>
</section>

<!-- イベントセクション -->
<section id="events" class="py-20 bg-gray-50">
	<div class="max-w-7xl mx-auto px-6">
		<div class="text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">イベント情報</h2>
			<p class="text-xl text-gray-600">3つの会場で多彩な体験をお楽しみください</p>
		</div>
		
		<div class="grid lg:grid-cols-3 gap-8">
			<div class="bg-white rounded-2xl overflow-hidden shadow-lg">
				<div class="h-48 bg-gradient-to-br from-blue-500 to-blue-600"></div>
				<div class="p-8">
					<h3 class="text-2xl font-bold text-gray-900 mb-4">エコールいずみ</h3>
					<p class="text-gray-600 mb-6">企業・地域の動画、当日パンフレットの販売</p>
				</div>
			</div>
			
			<div class="bg-white rounded-2xl overflow-hidden shadow-lg">
				<div class="h-48 bg-gradient-to-br from-green-500 to-green-600"></div>
				<div class="p-8">
					<h3 class="text-2xl font-bold text-gray-900 mb-4">桃山学院大学</h3>
					<p class="text-gray-600 mb-6">エレノア館・ヨハネ館でテクノロジー体験</p>
				</div>
			</div>
			
			<div class="bg-white rounded-2xl overflow-hidden shadow-lg">
				<div class="h-48 bg-gradient-to-br from-purple-500 to-purple-600"></div>
				<div class="p-8">
					<h3 class="text-2xl font-bold text-gray-900 mb-4">久保惣記念美術館</h3>
					<p class="text-gray-600 mb-6">伝統文化と芸術の展示・体験</p>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- パビリオンセクション -->
<section id="pavilions" class="py-20 bg-white">
	<div class="max-w-7xl mx-auto px-6">
		<div class="text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">パビリオン</h2>
			<p class="text-xl text-gray-600">和泉市の伝統文化、テクノロジー、コミュニティを体験できる多彩なパビリオンをご紹介</p>
		</div>

		<!-- 伝統文化パビリオン -->
		<div class="mb-16 bg-gradient-to-br from-red-50 via-pink-50 to-purple-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">伝統文化パビリオン</h3>
			<p class="text-lg text-gray-600 mb-8">伝統工芸体験、浮世絵刷り体験、ガラス玉ブレスレット作り、さをり織り体験など</p>
			<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
				<!-- パビリオンカード1 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-1.png" alt="井阪晴子" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">井阪硝子</h4>
					<p class="text-sm text-gray-600">伝統工芸の実演と体験</p>
				</div>

				<!-- パビリオンカード2 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-2.jpg" alt="佐竹ガラス" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">佐竹ガラス</h4>
					<p class="text-sm text-gray-600">ガラス工芸の体験</p>
				</div>

				<!-- パビリオンカード3 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-3.jpg" alt="和泉だんじり" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">和泉だんじり</h4>
					<p class="text-sm text-gray-600">だんじり文化の紹介</p>
				</div>

				<!-- パビリオンカード4 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-4.jpg" alt="さをり織り" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">さをり織り</h4>
					<p class="text-sm text-gray-600">織物の体験</p>
				</div>

				<!-- パビリオンカード5 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-5.jpg" alt="ガラス玉ブレスレット作り" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">ガラス玉ブレスレット</h4>
					<p class="text-sm text-gray-600">アクセサリー作り体験</p>
				</div>

				<!-- パビリオンカード6 -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/tradition-6.jpg" alt="久保惣記念美術館" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">久保惣記念美術館</h4>
					<p class="text-sm text-gray-600">浮世絵刷り体験</p>
				</div>
			</div>
		</div>

		<!-- テクノロジーパビリオン -->
		<div class="mb-16 bg-gradient-to-br from-blue-50 via-cyan-50 to-sky-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">テクノロジーパビリオン</h3>
			<p class="text-lg text-gray-600 mb-8">和泉市から世界に羽ばたく企業が一同に集合！大阪・関西万博度出展企業も多数参加</p>
			<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-7 gap-6">
				<!-- パビリオンカード -->
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-1.jpg" alt="ATTACCATO合同会社" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">ATTACCATO合同会社</h4>
					<p class="text-xs text-gray-600">最新技術の展示</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-2.jpg" alt="エースシステム株式会社" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">エースシステム株式会社</h4>
					<p class="text-xs text-gray-600">システム開発</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-3.jpg" alt="株式会社興徳クリーナー" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">株式会社興徳クリーナー</h4>
					<p class="text-xs text-gray-600">環境技術</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-4.jpg" alt="メディカルエイド株式会社" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">メディカルエイド株式会社</h4>
					<p class="text-xs text-gray-600">医療支援技術</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-5.jpg" alt="株式会社USEYA" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">株式会社USEYA</h4>
					<p class="text-xs text-gray-600">イノベーション</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-6.jpg" alt="大阪トヨペット" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">大阪トヨペット</h4>
					<p class="text-xs text-gray-600">モビリティ技術</p>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/tech-7.jpg" alt="大栄環境グループ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1 text-sm">大栄環境グループ</h4>
					<p class="text-xs text-gray-600">環境ソリューション</p>
				</div>
			</div>
		</div>

		<!-- コミュニティパビリオン -->
		<div class="mb-16 bg-gradient-to-br from-green-50 via-emerald-50 to-teal-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">コミュニティパビリオン</h3>
			<p class="text-lg text-gray-600 mb-8">コミュニティは地域支援と食品・物販など</p>
			<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-1.jpg" alt="なんよこPLAY PARK" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">なんよこPLAY PARK</h4>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-2.jpg" alt="地域拠点FLAT" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">地域拠点FLAT</h4>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-3.jpg" alt="企業主導型両親教室" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">企業主導型両親教室</h4>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-4.jpg" alt="稲空カフェ" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">稲空カフェ</h4>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-5.jpg" alt="自由帳" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">自由帳</h4>
				</div>

				<div class="group">
					<div class="bg-gray-100 rounded-xl overflow-hidden mb-3 aspect-square">
						<img src="/images/pavilions/community-6.jpg" alt="有新サービス" class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">有新サービス</h4>
				</div>
			</div>
		</div>

		<!-- 食・特産品パビリオン -->
		<div class="mb-16 bg-gradient-to-br from-orange-50 via-amber-50 to-yellow-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">食・特産品パビリオン</h3>
			<p class="text-lg text-gray-600 mb-8">和泉市の農業・特産品を知って・食べて・感じる未来</p>
			<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-1.jpg" alt="今井とうふ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">今井とうふ</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-2.jpg" alt="おに工房 花菜" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">おに工房 花菜</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-3.jpg" alt="オヤジのたまごループ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">オヤジのたまごループ</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-4.jpg" alt="Café FLAT" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">Café FLAT</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-5.jpg" alt="キノシタファーム" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">キノシタファーム</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="久保農園" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">久保農園</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="K.farm Musubi" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">K.farm Musubi</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="つじい農園" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">つじい農園</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="TETEONI" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">TETEONI</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="肉のばんば家" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">肉のばんば家</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="hachiiro" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">hachiiro</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="ふじわらのうえん" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">ふじわらのうえん</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="丸和食品株式会社" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">丸和食品株式会社</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="株式会社MealFarm" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">株式会社MealFarm</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="心寿" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">心寿</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-6.jpg" alt="シビスおくむら" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">シビスおくむら</h4>
				</div>
			</div>
		</div>

		<div class="mb-16 bg-gradient-to-br from-rose-50 via-red-50 to-orange-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">キッチンカー</h3>
			<p class="text-lg text-gray-600 mb-8">ワクワクおいしいキッチンカー</p>
			<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-1.jpg" alt="今井とうふ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">今井とうふ</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-2.jpg" alt="おに工房 花菜" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">おに工房 花菜</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-3.jpg" alt="オヤジのたまごループ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">オヤジのたまごループ</h4>
				</div>

				<div class="group">
					<div class="bg-amber-50 rounded-xl overflow-hidden mb-3 aspect-square flex items-center justify-center p-4">
						<img src="/images/pavilions/food-3.jpg" alt="オヤジのたまごループ" class="max-w-full max-h-full object-contain" on:error={handleImageError} />
					</div>
					<h4 class="font-bold text-gray-900 mb-1">オヤジのたまごループ</h4>
				</div>
			</div>
		</div>

		<div class="mb-16 bg-gradient-to-br from-indigo-50 via-violet-50 to-purple-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">大人のパビリオン</h3>
			<p class="text-lg text-gray-600 mb-8">お酒などのコンテンツを用意しています</p>
		</div>

		<div class="mb-16 bg-gradient-to-br from-pink-50 via-fuchsia-50 to-rose-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">音楽</h3>
			<p class="text-lg text-gray-600 mb-8">地域の方々の演奏をチャペルで行います</p>
		</div>

		<div class="bg-gradient-to-br from-slate-50 via-gray-50 to-zinc-50 rounded-3xl p-8">
			<h3 class="text-3xl font-bold text-gray-900 mb-8">プロジェクションマッピング</h3>
			<p class="text-lg text-gray-600 mb-8">桃山学院大学テック部の学生によるプロジェクションマッピング</p>
		</div>
	</div>
</section>

<!-- アクセスセクション -->
<section id="access" class="py-20 bg-gray-50">
	<div class="max-w-7xl mx-auto px-6">
		<div class="text-center mb-16">
			<h2 class="text-4xl md:text-5xl font-bold text-gray-900 mb-6">アクセス</h2>
		</div>
		
		<div class="grid lg:grid-cols-2 gap-12 items-center">
			<div>
				<h3 class="text-2xl font-bold text-gray-900 mb-6">開催日時・会場</h3>
				<div class="space-y-6">
					<div class="border-l-4 border-blue-500 pl-6">
						<h4 class="font-semibold text-lg text-gray-900">開催日</h4>
						<p class="text-gray-600">2025年10月25日（土）</p>
						<p class="text-gray-600">10時〜19時(展示は17時まで)</p>
					</div>
					
					<div class="border-l-4 border-green-500 pl-6">
						<h4 class="font-semibold text-lg text-gray-900">会場</h4>
						<ul class="text-gray-600 space-y-1">
							<li>• エコールいずみ</li>
							<li>• 桃山学院大学（エレノア館・ヨハネ館・バルナバ館・チャペル）</li>
							<li>• 久保惣記念美術館</li>
						</ul>
					</div>
				</div>
			</div>
			
			<div class="bg-gray-100 rounded-2xl p-8">
				<div class="h-64 bg-gray-300 rounded-lg flex items-center justify-center text-gray-500">
					<iframe src="https://www.google.com/maps/d/u/0/embed?mid=1m-6U2Ifh-1s5ghHsvdbYMI4NIgojmVk&ehbc=2E312F" width="100%" height="100%"></iframe>
				</div>
			</div>
		</div>
	</div>
</section>

<!-- お問い合わせセクション -->
<section id="contact" class="py-20 bg-blue-900 text-white">
	<div class="max-w-7xl mx-auto px-6 text-center">
		<h2 class="text-4xl md:text-5xl font-bold mb-6">お問い合わせ</h2>
		<p class="text-xl mb-12 opacity-90">ご質問やお問い合わせは以下からどうぞ</p>
		
		<div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 max-w-4xl mx-auto">
			<a href="mailto:info@izumi-expo.jp" class="bg-white/10 rounded-2xl p-6 hover:bg-white/20 transition-colors">
				<div class="w-12 h-12 bg-white/20 rounded-full mx-auto mb-4 flex items-center justify-center">
					<svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 4.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path>
					</svg>
				</div>
				<div class="text-sm font-semibold">Email</div>
			</a>
			
			<a href="https://lin.ee/8q17Rrv" class="bg-white/10 rounded-2xl p-6 hover:bg-white/20 transition-colors">
				<div class="w-12 h-12 bg-white/20 rounded-full mx-auto mb-4 flex items-center justify-center">
					<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
						<path d="M13.3 17.2c0-.4-.4-.8-.8-.8s-.8.3-.8.8c0 .4.4.8.8.8s.8-.4.8-.8zm-1.6 0c0-.4-.4-.8-.8-.8s-.8.3-.8.8c0 .4.4.8.8.8s.8-.4.8-.8zm-1.6 0c0-.4-.4-.8-.8-.8s-.8.3-.8.8c0 .4.4.8.8.8s.8-.4.8-.8z"/>
					</svg>
				</div>
				<div class="text-sm font-semibold">LINE</div>
			</a>
			
			<a href="https://instagram.com/izumi_expo" class="bg-white/10 rounded-2xl p-6 hover:bg-white/20 transition-colors">
				<div class="w-12 h-12 bg-white/20 rounded-full mx-auto mb-4 flex items-center justify-center">
					<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
						<path d="M12 2.2c3.2 0 3.6 0 4.9.1 1.2.1 1.8.2 2.2.4.6.2 1 .5 1.4.9.4.4.7.8.9 1.4.2.4.3 1 .4 2.2.1 1.3.1 1.7.1 4.9s0 3.6-.1 4.9c-.1 1.2-.2 1.8-.4 2.2-.2.6-.5 1-.9 1.4-.4.4-.8.7-1.4.9-.4.2-1 .3-2.2.4-1.3.1-1.7.1-4.9.1s-3.6 0-4.9-.1c-1.2-.1-1.8-.2-2.2-.4-.6-.2-1-.5-1.4-.9-.4-.4-.7-.8-.9-1.4-.2-.4-.3-1-.4-2.2-.1-1.3-.1-1.7-.1-4.9s0-3.6.1-4.9c.1-1.2.2-1.8.4-2.2.2-.6.5-1 .9-1.4.4-.4.8-.7 1.4-.9.4-.2 1-.3 2.2-.4 1.3-.1 1.7-.1 4.9-.1zm0-2.2c-3.3 0-3.7 0-5 .1-1.3.1-2.2.2-3 .5-.8.3-1.5.7-2.2 1.4-.7.7-1.1 1.4-1.4 2.2-.3.8-.4 1.7-.5 3-.1 1.3-.1 1.7-.1 5s0 3.7.1 5c.1 1.3.2 2.2.5 3 .3.8.7 1.5 1.4 2.2.7.7 1.4 1.1 2.2 1.4.8.3 1.7.4 3 .5 1.3.1 1.7.1 5 .1s3.7 0 5-.1c1.3-.1 2.2-.2 3-.5.8-.3 1.5-.7 2.2-1.4.7-.7 1.1-1.4 1.4-2.2.3-.8.4-1.7.5-3 .1-1.3.1-1.7.1-5s0-3.7-.1-5c-.1-1.3-.2-2.2-.5-3-.3-.8-.7-1.5-1.4-2.2-.7-.7-1.4-1.1-2.2-1.4-.8-.3-1.7-.4-3-.5-1.3-.1-1.7-.1-5-.1z"/>
						<path d="M12 5.8c-3.4 0-6.2 2.8-6.2 6.2s2.8 6.2 6.2 6.2 6.2-2.8 6.2-6.2-2.8-6.2-6.2-6.2zm0 10.2c-2.2 0-4-1.8-4-4s1.8-4 4-4 4 1.8 4 4-1.8 4-4 4zm6.4-11.8c-.8 0-1.4.6-1.4 1.4s.6 1.4 1.4 1.4 1.4-.6 1.4-1.4-.6-1.4-1.4-1.4z"/>
					</svg>
				</div>
				<div class="text-sm font-semibold">Instagram</div>
			</a>
			
			<a href="https://twitter.com/izumi_expo" class="bg-white/10 rounded-2xl p-6 hover:bg-white/20 transition-colors">
				<div class="w-12 h-12 bg-white/20 rounded-full mx-auto mb-4 flex items-center justify-center">
					<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
						<path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
					</svg>
				</div>
				<div class="text-sm font-semibold">X (Twitter)</div>
			</a>
		</div>
	</div>
</section>

<!-- フッター -->
<footer class="bg-gray-900 text-white py-12">
	<div class="max-w-7xl mx-auto px-6 text-center">
		<div class="text-2xl font-bold mb-4">いずみ万博 2025</div>
		<p class="text-gray-400 mb-6">いのち輝く未来社会のいずみ</p>
		<p class="text-sm text-gray-500">© 2025 いずみ万博実行委員会. All rights reserved.</p>
	</div>
</footer>