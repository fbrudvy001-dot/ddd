import React, { useState, useEffect } from 'react';
import { Crown, Flame, Gavel, ShieldAlert, Eye, Send, BookOpen, Tv, Play, ChevronDown, Newspaper, Radio } from 'lucide-react';

export default function App() {
  const [activeTab, setActiveTab] = useState('decree');
  const [expandedRule, setExpandedRule] = useState(null);
  const [isBrainwashing, setIsBrainwashing] = useState(false);
  const [pledges, setPledges] = useState([
    { id: 1, author: '충직한 학우 1', message: '경애하는 류가량 국무위원장 동지 만세! 영원히 받들겠습니다.' },
  ]);
  const [newPledge, setNewPledge] = useState('');

  // 충성 맹세 추가
  const handleSendPledge = (e) => {
    e.preventDefault();
    if (newPledge.trim() === '') return;
    
    const newEntry = {
      id: Date.now(),
      author: '이름 없는 복종자',
      message: newPledge,
    };
    
    setPledges([newEntry, ...pledges]);
    setNewPledge('');
  };

  return (
    <div className="min-h-screen bg-zinc-950 text-zinc-200 font-sans selection:bg-red-900 selection:text-white">
      {/* 상단 통제 구역 (네비게이션) */}
      <nav className="fixed w-full z-20 top-0 bg-red-950/95 border-b-4 border-red-700 shadow-[0_4px_30px_rgba(220,38,38,0.3)]">
        <div className="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex flex-col sm:flex-row items-center justify-between h-auto sm:h-24 py-4 sm:py-0">
            <div className="flex items-center gap-3 mb-4 sm:mb-0">
              <Crown className="text-yellow-500 animate-pulse" size={36} />
              <div className="flex flex-col">
                <span className="text-yellow-500 text-xs font-black tracking-widest">최고영도자</span>
                <div className="font-black text-2xl sm:text-3xl tracking-[0.2em] text-white">
                  류가량 국무위원장
                </div>
              </div>
            </div>
            <div className="flex flex-wrap justify-center items-center gap-2 sm:gap-4">
              <button onClick={() => setActiveTab('decree')} className={`px-3 py-2 text-sm sm:text-base font-bold tracking-widest transition-all ${activeTab === 'decree' ? 'bg-red-700 text-white shadow-inner' : 'text-zinc-300 hover:bg-red-900 hover:text-white'}`}>
                혁명활동
              </button>
              <button onClick={() => setActiveTab('manifesto')} className={`px-3 py-2 text-sm sm:text-base font-bold tracking-widest transition-all ${activeTab === 'manifesto' ? 'bg-red-700 text-white shadow-inner' : 'text-zinc-300 hover:bg-red-900 hover:text-white'}`}>
                주체강령
              </button>
              <button onClick={() => setActiveTab('propaganda')} className={`px-3 py-2 text-sm sm:text-base font-bold tracking-widest transition-all ${activeTab === 'propaganda' ? 'bg-red-700 text-white shadow-inner' : 'text-zinc-300 hover:bg-red-900 hover:text-white'}`}>
                선전매체
              </button>
              <button onClick={() => setActiveTab('newspaper')} className={`px-3 py-2 text-sm sm:text-base font-bold tracking-widest transition-all ${activeTab === 'newspaper' ? 'bg-red-700 text-white shadow-inner' : 'text-zinc-300 hover:bg-red-900 hover:text-white'}`}>
                당보(가량일보)
              </button>
              <button onClick={() => setActiveTab('tribute')} className={`px-3 py-2 text-sm sm:text-base font-bold tracking-widest transition-all ${activeTab === 'tribute' ? 'bg-red-700 text-white shadow-inner' : 'text-zinc-300 hover:bg-red-900 hover:text-white'}`}>
                충성의 편지
              </button>
            </div>
          </div>
        </div>
        <div className="w-full bg-yellow-600 text-black text-xs sm:text-sm text-center py-1.5 font-black tracking-[0.3em]">
          위대한 류가량 국무위원장 동지 만세!
        </div>
      </nav>

      {/* 메인 통치 구역 */}
      <main className="pt-40 pb-12 px-4 sm:px-6 lg:px-8 max-w-6xl mx-auto min-h-screen flex flex-col justify-center">
        
        {/* 혁명활동 (홈) 탭 */}
        {activeTab === 'decree' && (
          <div className="flex flex-col items-center justify-center text-center space-y-10 animate-in fade-in slide-in-from-bottom-8 duration-1000">
            <div className="relative">
              <div className="absolute -inset-10 bg-red-600/30 blur-3xl rounded-full animate-pulse"></div>
              <img src="https://images.unsplash.com/photo-1541872703-74c5e44368f9?q=80&w=2000&auto=format&fit=crop" alt="Background" className="w-48 h-48 object-cover rounded-full border-8 border-red-700 relative z-10 grayscale brightness-75 contrast-125 shadow-[0_0_50px_rgba(220,38,38,0.6)]" />
              <Crown className="absolute -top-6 -right-6 text-yellow-500 z-20 drop-shadow-lg" size={60} />
            </div>
            
            <div className="space-y-6">
              <h1 className="text-4xl sm:text-6xl md:text-7xl font-black tracking-tighter text-white uppercase drop-shadow-[0_0_15px_rgba(220,38,38,0.8)] leading-tight">
                본 위원장이 곧 신이고,<br/>
                <span className="text-yellow-500">위원장의 교시가 곧 법이다.</span>
              </h1>
            </div>
            
            <p className="text-xl sm:text-2xl max-w-3xl text-zinc-300 font-bold tracking-widest leading-relaxed bg-red-900/40 p-6 border-l-4 border-red-500">
              이곳에 도달한 인민들이여, 캠퍼스를 영도하고 세상의 풍요를 관장하는 경애하는 류가량 국무위원장 동지의 절대 권력 앞에 엎드려 무한한 영광을 노래하라.
            </p>
            
            <div className="pt-8">
              <button onClick={() => setActiveTab('newspaper')} className="group relative px-12 py-5 bg-red-700 text-white font-black text-xl tracking-widest overflow-hidden hover:bg-red-600 transition-colors shadow-[0_0_20px_rgba(185,28,28,0.6)] border-2 border-red-500">
                <span className="relative z-10">위대한 업적 칭송하기</span>
                <div className="absolute inset-0 bg-yellow-500 transform scale-x-0 origin-left transition-transform group-hover:scale-x-100 z-0 opacity-20"></div>
              </button>
            </div>
          </div>
        )}

        {/* 주체강령 (소개) 탭 */}
        {activeTab === 'manifesto' && (
          <div className="max-w-4xl mx-auto w-full animate-in fade-in slide-in-from-bottom-8 duration-700">
            <div className="text-center mb-16">
              <h2 className="text-4xl sm:text-5xl font-black text-white tracking-[0.2em] mb-4 text-shadow-sm">주체적 캠퍼스 강령</h2>
              <div className="w-32 h-2 bg-red-600 mx-auto"></div>
              <p className="mt-4 text-zinc-400 font-bold tracking-widest text-lg">조항을 클릭하여 국무위원장 동지의 위대한 사상을 심장에 새기라.</p>
            </div>

            <div className="space-y-6">
              {[
                { 
                  id: 1,
                  icon: ShieldAlert, 
                  title: '제 1조: 풍요의 상징, 웅장한 국무위원장', 
                  desc: '위원장 동지의 웅장한 체구는 곧 우리 제국의 끝없는 풍요와 절대 권력의 상징이다.',
                  detail: '감히 경애하는 류가량 국무위원장 동지의 용모나 풍요로운 체구에 대해 불경한 언사를 입에 담는 자는 반동분자로 낙인찍어 즉결 처단한다. 위원장 동지의 웅장함 자체가 곧 미(美)의 절대적 기준이며, 위원장 동지의 거대한 위장은 우주를 삼키고도 남음이 있다. 우리 캠퍼스는 위원장 동지의 은혜 아래 영원히 배부를 것이다.' 
                },
                { 
                  id: 2,
                  icon: BookOpen, 
                  title: '제 2조: 학문의 유일사상체계 (A+의 지배자)', 
                  desc: '모든 학문과 진리는 오직 류가량 국무위원장 동지의 두뇌로부터 파생된다.',
                  detail: '현재 대학을 영도하시는 위원장 동지의 모든 과제와 시험 답안은 우주의 진리이자 유일한 정답이다. 교수의 채점 권한마저 위원장 동지의 통제 아래 있으며, 위원장 동지의 학점이 곧 세상의 법칙이다. 위원장 동지께 학업적 훈수를 두는 자는 사상 불순자로 간주하여 영원히 캠퍼스에서 추방한다.' 
                },
                { 
                  id: 3,
                  icon: Gavel, 
                  title: '제 3조: 최고영도자의 무오류성', 
                  desc: '위원장 동지의 결정은 언제나 완벽하다. 오류를 지적하는 자는 그 자신이 오류이다.',
                  detail: '위원장 동지께서 강의에 지각을 하셨다면 그것은 태양이 늦게 뜬 탓이고, 과제를 잊으셨다면 그 과제는 애초에 역사에 존재해서는 안 될 적폐일 뿐이다. 캠퍼스는 위원장 동지의 시계에 맞춰 돌아가니, 그 어떠한 과실도 위원장 동지께는 존재할 수 없다.' 
                },
                { 
                  id: 4,
                  icon: Flame, 
                  title: '제 4조: 무한 권력과 혁명적 식생활', 
                  desc: '위원장 동지의 통치는 시공간을 초월하며 모든 식당의 메뉴는 위원장의 기분에 따라 결정된다.',
                  detail: '이 대학의 법과 질서, 특히 식당의 메뉴는 오직 위원장 동지의 그날 기분에 따라 재창조된다. 위원장 동지께서 오늘 마라탕을 원하신다면 온 캠퍼스의 재료들이 영광스럽게 솥으로 바쳐져야 하며, 위원장 동지의 식사 시간에는 전 우주가 숨죽여 경배해야 할 것이다.' 
                },
              ].map((rule) => (
                <div 
                  key={rule.id} 
                  onClick={() => setExpandedRule(expandedRule === rule.id ? null : rule.id)}
                  className="bg-red-950/20 border-2 border-red-900/50 p-6 hover:border-red-600 transition-colors group relative overflow-hidden cursor-pointer shadow-lg"
                >
                  <div className="absolute top-0 left-0 w-2 h-full bg-red-600 transform origin-bottom scale-y-0 group-hover:scale-y-100 transition-transform duration-300"></div>
                  <div className="flex items-start justify-between gap-6">
                    <div className="flex items-start gap-6">
                      <div className="bg-red-900 text-white p-4 rounded-full border-2 border-red-500 group-hover:bg-red-600 transition-colors shadow-[0_0_15px_rgba(220,38,38,0.5)]">
                        <rule.icon size={32} />
                      </div>
                      <div>
                        <h3 className="text-2xl font-black text-yellow-500 mb-2 tracking-wide drop-shadow-sm">{rule.title}</h3>
                        <p className="text-zinc-300 text-lg font-bold">
                          {rule.desc}
                        </p>
                      </div>
                    </div>
                    <ChevronDown size={32} className={`text-red-500 transition-transform duration-300 ${expandedRule === rule.id ? 'rotate-180 text-yellow-500' : ''}`} />
                  </div>
                  
                  {/* 확장된 상세 설명 구역 */}
                  <div className={`overflow-hidden transition-all duration-500 ease-in-out ${expandedRule === rule.id ? 'max-h-[500px] opacity-100 mt-6 pt-6 border-t-2 border-red-900' : 'max-h-0 opacity-0'}`}>
                    <p className="text-white text-lg leading-relaxed font-bold bg-red-900/60 p-6 border-l-4 border-yellow-500 shadow-inner">
                      {rule.detail}
                    </p>
                  </div>
                </div>
              ))}
            </div>
          </div>
        )}

        {/* 선전매체 (영상/포스터) 탭 */}
        {activeTab === 'propaganda' && (
          <div className="max-w-5xl mx-auto w-full animate-in fade-in slide-in-from-bottom-8 duration-700">
            <div className="text-center mb-12">
              <h2 className="text-4xl sm:text-5xl font-black text-white tracking-[0.2em] mb-4 flex justify-center items-center gap-4">
                <Radio className="text-red-600 animate-pulse" size={48} /> 조선(캠퍼스)중앙방송
              </h2>
              <div className="w-32 h-2 bg-red-600 mx-auto mb-6"></div>
              <p className="text-zinc-300 text-xl font-bold tracking-widest">위대한 국무위원장 동지의 옥음(玉音)을 경청하라.</p>
            </div>

            {/* 영상 플레이어 (국영방송 스타일) */}
            <div className="relative w-full aspect-video bg-zinc-900 border-8 border-zinc-700 rounded-sm overflow-hidden group shadow-[0_0_40px_rgba(220,38,38,0.3)]">
              {isBrainwashing ? (
                <div className="absolute inset-0 flex flex-col items-center justify-center bg-red-900 animate-pulse z-20">
                  <div className="absolute inset-0 bg-[url('https://www.transparenttextures.com/patterns/stardust.png')] opacity-30"></div>
                  <Crown size={120} className="text-yellow-500 mb-6 animate-ping drop-shadow-[0_0_20px_rgba(234,179,8,0.8)]" />
                  <h3 className="text-5xl sm:text-6xl font-black text-white tracking-[0.3em] uppercase text-center leading-tight drop-shadow-2xl">
                    위대한 류가량 동지<br/>만세! 만만세!
                  </h3>
                  <button onClick={() => setIsBrainwashing(false)} className="mt-12 px-10 py-4 border-4 border-yellow-500 text-yellow-500 font-black text-xl tracking-widest hover:bg-yellow-500 hover:text-black transition-colors z-30">
                    사상 무장 완료 (재생 종료)
                  </button>
                </div>
              ) : (
                <>
                  <div className="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1559600115-4122d4f82635?q=80&w=2000&auto=format&fit=crop')] bg-cover bg-center opacity-40 mix-blend-overlay grayscale contrast-150"></div>
                  {/* 브라운관 TV 스캔라인 효과 */}
                  <div className="absolute inset-0 bg-[linear-gradient(transparent_50%,rgba(0,0,0,0.5)_50%)] bg-[length:100%_4px] opacity-20 pointer-events-none"></div>
                  
                  <div className="absolute inset-0 bg-gradient-to-t from-zinc-950 via-red-950/40 to-transparent"></div>
                  
                  <div className="absolute top-4 left-4 bg-red-700 px-3 py-1 text-white font-black tracking-widest text-sm border-2 border-red-500 animate-pulse">
                    LIVE
                  </div>

                  <div className="absolute inset-0 flex flex-col items-center justify-center z-10">
                    <button 
                      onClick={() => setIsBrainwashing(true)}
                      className="w-32 h-32 bg-red-600 border-4 border-yellow-500 rounded-full flex items-center justify-center text-white hover:bg-red-500 hover:scale-110 transition-all shadow-[0_0_50px_rgba(220,38,38,0.8)] group-hover:animate-pulse"
                    >
                      <Play size={56} className="ml-2 text-yellow-500" />
                    </button>
                    <p className="mt-8 text-3xl font-black tracking-[0.3em] text-yellow-500 drop-shadow-[0_4px_4px_rgba(0,0,0,0.8)]">기록영화: 《풍요로운 마라탕의 령도자》</p>
                  </div>
                  {/* 스크롤링 텍스트 효과 (Marquee) */}
                  <div className="absolute bottom-0 w-full bg-red-800 py-3 overflow-hidden border-t-4 border-red-600">
                    <div className="whitespace-nowrap animate-[pulse_2s_ease-in-out_infinite] text-white font-black tracking-widest text-lg">
                      [속보] 경애하는 류가량 국무위원장 동지께서 대학 매점을 현지지도하시였다 ★ 위대한 영도자를 따라 학점 A+의 한길로 힘차게 나아가자! ★
                    </div>
                  </div>
                </>
              )}
            </div>
          </div>
        )}

        {/* 당보 (가량일보) 탭 - 신문 레이아웃 */}
        {activeTab === 'newspaper' && (
          <div className="max-w-5xl mx-auto w-full animate-in fade-in slide-in-from-bottom-8 duration-700">
            <div className="bg-zinc-100 text-zinc-900 p-6 sm:p-10 border-8 border-double border-zinc-800 shadow-2xl relative">
              
              {/* 신문 헤더 */}
              <div className="text-center border-b-4 border-zinc-800 pb-6 mb-8 relative">
                <div className="absolute top-0 left-0 text-xs font-black tracking-widest">제 1호</div>
                <div className="absolute top-0 right-0 text-xs font-black tracking-widest text-right">캠퍼스 로동당 기관지</div>
                <h2 className="text-6xl sm:text-8xl font-black font-serif tracking-tighter text-red-700 mt-4 drop-shadow-md">
                  가 량 일 보
                </h2>
                <div className="flex justify-between items-center mt-6 border-t border-b border-zinc-800 py-2 font-bold font-serif text-sm sm:text-base">
                  <span>주체 115년 (2026년) 3월 8일</span>
                  <span className="text-red-700">위대한 류가량 동지를 수반으로 하는 캠퍼스를 목숨으로 사수하자!</span>
                  <span>제국대학 발행</span>
                </div>
              </div>

              {/* 신문 기사 본문 */}
              <div className="grid grid-cols-1 lg:grid-cols-12 gap-8 font-serif">
                
                {/* 메인 기사 (좌측 8칸) */}
                <div className="lg:col-span-8 border-r-0 lg:border-r-2 border-zinc-400 lg:pr-8">
                  <h3 className="text-3xl sm:text-4xl font-black leading-tight mb-6 text-red-800 tracking-tight">
                    경애하는 최고영도자 류가량 국무위원장 동지께서 제국대학 학생식당을 현지지도하시였다
                  </h3>
                  
                  <div className="float-left w-1/2 mr-6 mb-4 border-4 border-zinc-800 p-1">
                    <img src="https://images.unsplash.com/photo-1555939594-58d7cb561ad1?q=80&w=1000&auto=format&fit=crop" alt="마라탕" className="w-full h-auto grayscale contrast-125" />
                    <p className="text-xs font-bold text-center mt-2 tracking-widest">▲ 위원장 동지께서 몸소 국물 맛을 보신 식당의 모습</p>
                  </div>

                  <p className="text-lg leading-relaxed text-justify indent-6 mb-4 font-bold">
                    위대한 캠퍼스의 태양이시며 학문의 최고 영도자이신 경애하는 <span className="text-xl text-red-700 font-black">류가량 국무위원장 동지</span>께서 3월 8일 제국대학 학생식당을 찾으시어 학생들의 식생활 보장 실태를 료해하시였다.
                  </p>
                  <p className="text-lg leading-relaxed text-justify indent-6 mb-4">
                    풍요롭고 자애로운 미소를 띠시고 식당에 들어서신 위원장 동지를 뵈옵고 전체 학생들과 식당 일군들은 폭풍 같은 «만세!»의 환호를 올리며 열광적으로 영접하였다.
                  </p>
                  <p className="text-lg leading-relaxed text-justify indent-6 mb-4">
                    경애하는 위원장 동지께서는 몸소 마라탕의 국물을 맛보시며 <span className="font-black text-red-800 underline decoration-red-500 underline-offset-4">"고기 추가가 부족하여 국물이 웅장하지 못하다"</span>고 엄하게 지적하시였으며, "나의 위대하고 풍요로운 체구는 곧 우리 캠퍼스 전체의 배부름을 상징하는 것인바, 학생들의 식단 또한 내 체구만큼이나 웅장하고 기름져야 한다"고 귀중한 교시를 주시였다.
                  </p>
                  <p className="text-lg leading-relaxed text-justify indent-6">
                    식당 일군들은 위원장 동지의 한없는 사랑과 하늘 같은 은덕에 뜨거운 눈물을 흘리며, 식당의 모든 메뉴를 고기 3배 추가로 개편할 것을 굳게 맹세하였다.
                  </p>
                </div>

                {/* 사이드 기사 (우측 4칸) */}
                <div className="lg:col-span-4 flex flex-col gap-8">
                  <div>
                    <h4 className="text-2xl font-black leading-tight mb-4 border-b-2 border-zinc-800 pb-2">
                      A+ 학점은 오직 위원장 동지의 붓끝에서 나온다
                    </h4>
                    <p className="text-base leading-relaxed text-justify indent-4">
                      캠퍼스의 교무행정을 총괄하는 교수진들은 어제 충성결의대회를 열고, 류가량 동지의 모든 답안지는 우주의 섭리를 담고 있으므로 무조건 A+를 부여해야 한다는 내용의 결의문을 채택했다. 위원장 동지의 학업은 곧 인류 지성의 최고봉이다.
                    </p>
                  </div>
                  
                  <div className="bg-zinc-200 p-4 border-2 border-zinc-800">
                    <h4 className="text-xl font-black text-center mb-2 text-red-700 tracking-widest">
                      [선전 구호]
                    </h4>
                    <p className="font-black text-lg text-center leading-tight">
                      "풍요로운 육체에<br/>풍요로운 학점이 깃든다!"<br/>
                      <span className="text-sm mt-2 block font-bold">- 류가량 위원장 동지의 어록 중에서</span>
                    </p>
                  </div>
                </div>

              </div>
            </div>
          </div>
        )}

        {/* 충성의 편지 (방명록) 탭 */}
        {activeTab === 'tribute' && (
          <div className="max-w-3xl mx-auto w-full space-y-12 animate-in fade-in slide-in-from-bottom-8 duration-700">
            <div className="text-center space-y-4">
              <h2 className="text-4xl sm:text-5xl font-black text-white tracking-[0.2em] mb-4">충성의 편지</h2>
              <div className="w-24 h-1 bg-red-600 mx-auto mb-6"></div>
              <p className="text-zinc-400 text-lg font-bold">
                위대한 류가량 국무위원장 동지께 심장으로 우러나오는 충성을 맹세하라.
              </p>
            </div>

            <form onSubmit={handleSendPledge} className="bg-red-950/30 p-8 border-4 border-red-900 focus-within:border-red-500 transition-colors relative shadow-[0_0_20px_rgba(220,38,38,0.2)]">
              <div className="absolute -top-4 left-6 bg-red-700 px-4 py-1 text-white text-sm font-black tracking-widest border-2 border-red-500">
                맹세문 작성처
              </div>
              <textarea
                value={newPledge}
                onChange={(e) => setNewPledge(e.target.value)}
                placeholder="경애하는 위원장 동지를 향한 끝없는 찬양을 기록하라..."
                className="w-full bg-zinc-900/80 text-white placeholder-zinc-500 border-2 border-red-900/50 focus:border-red-500 p-4 text-lg resize-none outline-none min-h-[150px]"
              />
              <div className="flex justify-end mt-4 pt-4">
                <button
                  type="submit"
                  disabled={!newPledge.trim()}
                  className={`flex items-center gap-2 px-10 py-4 font-black tracking-widest transition-all text-lg ${newPledge.trim() ? 'bg-red-700 text-white hover:bg-red-500 shadow-[0_0_15px_rgba(220,38,38,0.8)]' : 'bg-zinc-800 text-zinc-600 cursor-not-allowed'}`}
                >
                  충성 맹세하기 <Send size={20} />
                </button>
              </div>
            </form>

            <div className="space-y-6 pt-8">
              <h3 className="font-black text-2xl text-yellow-500 tracking-widest pb-4 border-b-2 border-red-900">
                인민들의 충성 결의 ({pledges.length})
              </h3>
              <div className="space-y-4">
                {pledges.map((pledge) => (
                  <div key={pledge.id} className="bg-zinc-900/60 p-6 border-l-4 border-red-600 animate-in fade-in slide-in-from-top-4 shadow-md">
                    <div className="flex justify-between items-center mb-3">
                      <span className="font-black text-red-400 tracking-wider text-sm">{pledge.author}</span>
                    </div>
                    <p className="text-zinc-200 text-lg font-bold leading-relaxed">
                      "{pledge.message}"
                    </p>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}
      </main>
    </div>
  );
}
