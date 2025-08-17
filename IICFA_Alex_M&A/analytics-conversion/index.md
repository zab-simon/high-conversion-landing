import React, { useState } from 'react';
import { BarChart, Bar, XAxis, YAxis, CartesianGrid, Tooltip, ResponsiveContainer, LineChart, Line, PieChart, Pie, Cell, RadialBarChart, RadialBar, AreaChart, Area } from 'recharts';
import { AlertTriangle, CheckCircle, Target, TrendingUp, Users, DollarSign, Clock, Star } from 'lucide-react';

const ConversionAnalysisDashboard = () => {
  const [activeTab, setActiveTab] = useState('problems');

  // Данные для графиков
  const currentMetrics = [
    { name: 'Конверсия', current: 0.8, target: 3.5, improvement: 337 },
    { name: 'Лиды/день', current: 2, target: 8, improvement: 300 },
    { name: 'Качество лидов', current: 30, target: 65, improvement: 117 },
    { name: 'Время отклика', current: 24, target: 2, improvement: -92 }
  ];

  const conversionForecast = [
    { month: 'Сейчас', conversion: 0.8, leads: 2, sales: 0.3 },
    { month: '1 мес', conversion: 2.0, leads: 5, sales: 1.2 },
    { month: '3 мес', conversion: 2.8, leads: 7, sales: 2.1 },
    { month: '6 мес', conversion: 3.5, leads: 8, sales: 3.2 },
    { month: '12 мес', conversion: 4.2, leads: 12, sales: 5.8 }
  ];

  const problemsData = [
    { problem: 'Нет CTA', impact: 85, urgency: 95 },
    { problem: 'Слабый дизайн', impact: 70, urgency: 60 },
    { problem: 'Нет доверия', impact: 90, urgency: 85 },
    { problem: 'Плохая структура', impact: 75, urgency: 70 },
    { problem: 'Нет мобильной версии', impact: 80, urgency: 90 }
  ];

  const solutionsROI = [
    { solution: 'CTA кнопки', cost: 50, roi: 320, time: 1 },
    { solution: 'Редизайн', cost: 300, roi: 280, time: 4 },
    { solution: 'Кейсы и отзывы', cost: 100, roi: 250, time: 2 },
    { solution: 'Мобильная версия', cost: 150, roi: 200, time: 3 },
    { solution: 'SEO оптимизация', cost: 80, roi: 180, time: 6 }
  ];

  const priorityMatrix = [
    { name: 'CTA кнопки', impact: 95, effort: 20, color: '#FF6B6B' },
    { name: 'Контактные формы', impact: 85, effort: 30, color: '#FF6B6B' },
    { name: 'Лид-магниты', impact: 80, effort: 40, color: '#4ECDC4' },
    { name: 'Кейсы успеха', impact: 75, effort: 60, color: '#4ECDC4' },
    { name: 'Редизайн сайта', impact: 90, effort: 85, color: '#45B7D1' },
    { name: 'SEO оптимизация', impact: 60, effort: 70, color: '#96CEB4' }
  ];

  const budgetBreakdown = [
    { name: 'Дизайн и разработка', value: 500, color: '#FF6B6B' },
    { name: 'Контент и копирайт', value: 150, color: '#4ECDC4' },
    { name: 'Интеграции', value: 200, color: '#45B7D1' },
    { name: 'Маркетинг', value: 150, color: '#F7DC6F' }
  ];

  const competitorComparison = [
    { metric: 'Конверсия сайта', iicfa: 0.8, competitor1: 2.5, competitor2: 3.2, industry: 2.8 },
    { metric: 'Время загрузки', iicfa: 4.2, competitor1: 2.1, competitor2: 1.8, industry: 2.5 },
    { metric: 'Мобильность', iicfa: 20, competitor1: 85, competitor2: 92, industry: 78 },
    { metric: 'UX Score', iicfa: 45, competitor1: 78, competitor2: 85, industry: 72 }
  ];

  const COLORS = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#F7DC6F', '#BB8FCE'];

  return (
    <div className="min-h-screen bg-gradient-to-br from-purple-900 via-blue-900 to-indigo-900 p-6">
      <div className="max-w-7xl mx-auto">
        {/* Заголовок */}
        <div className="text-center mb-8">
          <h1 className="text-4xl font-bold text-white mb-4">
            🚀 Анализ конверсии IICFA.ru
          </h1>
          <p className="text-xl text-gray-300">
            Комплексный анализ и рекомендации для повышения конверсии
          </p>
        </div>

        {/* Навигация */}
        <div className="flex justify-center mb-8">
          <div className="bg-white/10 backdrop-blur-sm rounded-lg p-2 flex space-x-2">
            {[
              { id: 'problems', label: '❌ Проблемы', color: 'from-red-500 to-red-600' },
              { id: 'solutions', label: '✅ Решения', color: 'from-green-500 to-green-600' },
              { id: 'forecast', label: '📈 Прогноз', color: 'from-blue-500 to-blue-600' },
              { id: 'priority', label: '🎯 Приоритеты', color: 'from-purple-500 to-purple-600' }
            ].map((tab) => (
              <button
                key={tab.id}
                onClick={() => setActiveTab(tab.id)}
                className={`px-6 py-3 rounded-lg font-semibold transition-all ${
                  activeTab === tab.id
                    ? `bg-gradient-to-r ${tab.color} text-white shadow-lg`
                    : 'text-gray-300 hover:text-white hover:bg-white/10'
                }`}
              >
                {tab.label}
              </button>
            ))}
          </div>
        </div>

        {/* Основные метрики */}
        <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
          {currentMetrics.map((metric, index) => (
            <div key={metric.name} className="bg-gradient-to-br from-white/20 to-white/10 backdrop-blur-sm rounded-xl p-6 border border-white/20">
              <div className="flex items-center justify-between mb-4">
                <h3 className="text-white font-semibold">{metric.name}</h3>
                {index === 0 && <TrendingUp className="text-green-400" />}
                {index === 1 && <Users className="text-blue-400" />}
                {index === 2 && <Star className="text-yellow-400" />}
                {index === 3 && <Clock className="text-red-400" />}
              </div>
              <div className="space-y-2">
                <div className="flex justify-between">
                  <span className="text-gray-300">Сейчас:</span>
                  <span className="text-red-400 font-bold">{metric.current}{index === 3 ? 'ч' : index === 0 ? '%' : ''}</span>
                </div>
                <div className="flex justify-between">
                  <span className="text-gray-300">Цель:</span>
                  <span className="text-green-400 font-bold">{metric.target}{index === 3 ? 'ч' : index === 0 ? '%' : ''}</span>
                </div>
                <div className="flex justify-between">
                  <span className="text-gray-300">Рост:</span>
                  <span className={`font-bold ${metric.improvement > 0 ? 'text-green-400' : 'text-red-400'}`}>
                    {metric.improvement > 0 ? '+' : ''}{metric.improvement}%
                  </span>
                </div>
              </div>
            </div>
          ))}
        </div>

        {/* Контент по табам */}
        {activeTab === 'problems' && (
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
            {/* Анализ проблем */}
            <div className="bg-gradient-to-br from-red-500/20 to-red-600/10 backdrop-blur-sm rounded-xl p-6 border border-red-500/30">
              <h2 className="text-2xl font-bold text-white mb-6 flex items-center">
                <AlertTriangle className="mr-3 text-red-400" />
                Критические проблемы
              </h2>
              <ResponsiveContainer width="100%" height={300}>
                <BarChart data={problemsData}>
                  <CartesianGrid strokeDasharray="3 3" stroke="#ffffff20" />
                  <XAxis dataKey="problem" tick={{ fill: '#fff', fontSize: 12 }} angle={-45} textAnchor="end" height={80} />
                  <YAxis tick={{ fill: '#fff' }} />
                  <Tooltip 
                    contentStyle={{ 
                      backgroundColor: 'rgba(0,0,0,0.8)', 
                      border: 'none', 
                      borderRadius: '8px',
                      color: '#fff'
                    }} 
                  />
                  <Bar dataKey="impact" fill="#FF6B6B" name="Влияние на конверсию %" />
                  <Bar dataKey="urgency" fill="#FF9999" name="Срочность %" />
                </BarChart>
              </ResponsiveContainer>
            </div>

            {/* Сравнение с конкурентами */}
            <div className="bg-gradient-to-br from-blue-500/20 to-blue-600/10 backdrop-blur-sm rounded-xl p-6 border border-blue-500/30">
              <h2 className="text-2xl font-bold text-white mb-6">
                📊 Сравнение с конкурентами
              </h2>
              <ResponsiveContainer width="100%" height={300}>
                <BarChart data={competitorComparison}>
                  <CartesianGrid strokeDasharray="3 3" stroke="#ffffff20" />
                  <XAxis dataKey="metric" tick={{ fill: '#fff', fontSize: 12 }} angle={-45} textAnchor="end" height={80} />
                  <YAxis tick={{ fill: '#fff' }} />
                  <Tooltip 
                    contentStyle={{ 
                      backgroundColor: 'rgba(0,0,0,0.8)', 
                      border: 'none', 
                      borderRadius: '8px',
                      color: '#fff'
                    }} 
                  />
                  <Bar dataKey="iicfa" fill="#FF6B6B" name="IICFA" />
                  <Bar dataKey="competitor1" fill="#4ECDC4" name="Конкурент 1" />
                  <Bar dataKey="competitor2" fill="#45B7D1" name="Конкурент 2" />
                  <Bar dataKey="industry" fill="#F7DC6F" name="Среднее по отрасли" />
                </BarChart>
              </ResponsiveContainer>
            </div>
          </div>
        )}

        {activeTab === 'solutions' && (
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
            {/* ROI решений */}
            <div className="bg-gradient-to-br from-green-500/20 to-green-600/10 backdrop-blur-sm rounded-xl p-6 border border-green-500/30">
              <h2 className="text-2xl font-bold text-white mb-6 flex items-center">
                <CheckCircle className="mr-3 text-green-400" />
                ROI решений
              </h2>
              <ResponsiveContainer width="100%" height={300}>
                <AreaChart data={solutionsROI}>
                  <CartesianGrid strokeDasharray="3 3" stroke="#ffffff20" />
                  <XAxis dataKey="solution" tick={{ fill: '#fff', fontSize: 12 }} angle={-45} textAnchor="end" height={80} />
                  <YAxis tick={{ fill: '#fff' }} />
                  <Tooltip 
                    contentStyle={{ 
                      backgroundColor: 'rgba(0,0,0,0.8)', 
                      border: 'none', 
                      borderRadius: '8px',
                      color: '#fff'
                    }} 
                  />
                  <Area type="monotone" dataKey="roi" stroke="#4ECDC4" fill="#4ECDC4" fillOpacity={0.6} name="ROI %" />
                </AreaChart>
              </ResponsiveContainer>
            </div>

            {/* Бюджет */}
            <div className="bg-gradient-to-br from-yellow-500/20 to-yellow-600/10 backdrop-blur-sm rounded-xl p-6 border border-yellow-500/30">
              <h2 className="text-2xl font-bold text-white mb-6 flex items-center">
                <DollarSign className="mr-3 text-yellow-400" />
                Распределение бюджета
              </h2>
              <ResponsiveContainer width="100%" height={300}>
                <PieChart>
                  <Pie
                    data={budgetBreakdown}
                    cx="50%"
                    cy="50%"
                    labelLine={false}
                    label={({ name, value }) => `${name}: ${value}k`}
                    outerRadius={80}
                    fill="#8884d8"
                    dataKey="value"
                  >
                    {budgetBreakdown.map((entry, index) => (
                      <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                    ))}
                  </Pie>
                  <Tooltip 
                    contentStyle={{ 
                      backgroundColor: 'rgba(0,0,0,0.8)', 
                      border: 'none', 
                      borderRadius: '8px',
                      color: '#fff'
                    }} 
                  />
                </PieChart>
              </ResponsiveContainer>
            </div>
          </div>
        )}

        {activeTab === 'forecast' && (
          <div className="grid grid-cols-1 gap-8">
            {/* Прогноз конверсии */}
            <div className="bg-gradient-to-br from-blue-500/20 to-blue-600/10 backdrop-blur-sm rounded-xl p-6 border border-blue-500/30">
              <h2 className="text-2xl font-bold text-white mb-6 flex items-center">
                <TrendingUp className="mr-3 text-blue-400" />
                Прогноз роста показателей
              </h2>
              <ResponsiveContainer width="100%" height={400}>
                <LineChart data={conversionForecast}>
                  <CartesianGrid strokeDasharray="3 3" stroke="#ffffff20" />
                  <XAxis dataKey="month" tick={{ fill: '#fff' }} />
                  <YAxis tick={{ fill: '#fff' }} />
                  <Tooltip 
                    contentStyle={{ 
                      backgroundColor: 'rgba(0,0,0,0.8)', 
                      border: 'none', 
                      borderRadius: '8px',
                      color: '#fff'
                    }} 
                  />
                  <Line type="monotone" dataKey="conversion" stroke="#4ECDC4" strokeWidth={3} name="Конверсия %" />
                  <Line type="monotone" dataKey="leads" stroke="#FF6B6B" strokeWidth={3} name="Лиды/день" />
                  <Line type="monotone" dataKey="sales" stroke="#F7DC6F" strokeWidth={3} name="Продажи/день" />
                </LineChart>
              </ResponsiveContainer>
            </div>

            {/* Финансовый прогноз */}
            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              <div className="bg-gradient-to-br from-green-500/20 to-green-600/10 backdrop-blur-sm rounded-xl p-6 border border-green-500/30 text-center">
                <h3 className="text-xl font-bold text-white mb-4">💰 Прогноз дохода</h3>
                <div className="text-3xl font-bold text-green-400 mb-2">+580%</div>
                <p className="text-gray-300">Рост через 12 месяцев</p>
              </div>
              <div className="bg-gradient-to-br from-blue-500/20 to-blue-600/10 backdrop-blur-sm rounded-xl p-6 border border-blue-500/30 text-center">
                <h3 className="text-xl font-bold text-white mb-4">⏱️ Окупаемость</h3>
                <div className="text-3xl font-bold text-blue-400 mb-2">2-3 мес</div>
                <p className="text-gray-300">Полная окупаемость</p>
              </div>
              <div className="bg-gradient-to-br from-purple-500/20 to-purple-600/10 backdrop-blur-sm rounded-xl p-6 border border-purple-500/30 text-center">
                <h3 className="text-xl font-bold text-white mb-4">📈 ROI</h3>
                <div className="text-3xl font-bold text-purple-400 mb-2">320%</div>
                <p className="text-gray-300">Возврат инвестиций</p>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'priority' && (
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
            {/* Матрица приоритетов */}
            <div className="bg-gradient-to-br from-purple-500/20 to-purple-600/10 backdrop-blur-sm rounded-xl p-6 border border-purple-500/30">
              <h2 className="text-2xl font-bold text-white mb-6 flex items-center">
                <Target className="mr-3 text-purple-400" />
                Матрица приоритетов
              </h2>
              <div className="relative">
                <ResponsiveContainer width="100%" height={300}>
                  <ResponsiveContainer width="100%" height={300}>
                    <AreaChart data={[{impact: 0, effort: 0}, {impact: 100, effort: 100}]}>
                      <CartesianGrid strokeDasharray="3 3" stroke="#ffffff20" />
                      <XAxis 
                        dataKey="effort" 
                        tick={{ fill: '#fff' }} 
                        label={{ value: 'Сложность реализации →', position: 'insideBottom', offset: -5, style: { textAnchor: 'middle', fill: '#fff' } }}
                        domain={[0, 100]}
                      />
                      <YAxis 
                        dataKey="impact" 
                        tick={{ fill: '#fff' }} 
                        label={{ value: '↑ Влияние на конверсию', angle: -90, position: 'insideLeft', style: { textAnchor: 'middle', fill: '#fff' } }}
                        domain={[0, 100]}
                      />
                      <Tooltip 
                        contentStyle={{ 
                          backgroundColor: 'rgba(0,0,0,0.8)', 
                          border: 'none', 
                          borderRadius: '8px',
                          color: '#fff'
                        }} 
                      />
                    </AreaChart>
                  </ResponsiveContainer>
                </ResponsiveContainer>
                <div className="absolute inset-0">
                  {priorityMatrix.map((item, index) => (
                    <div
                      key={item.name}
                      className="absolute w-3 h-3 rounded-full transform -translate-x-1/2 -translate-y-1/2 cursor-pointer"
                      style={{
                        backgroundColor: item.color,
                        left: `${(item.effort / 100) * 100}%`,
                        bottom: `${(item.impact / 100) * 100}%`,
                        boxShadow: '0 0 10px rgba(255,255,255,0.5)'
                      }}
                      title={item.name}
                    />
                  ))}
                </div>
              </div>
              <div className="mt-4 space-y-2">
                {priorityMatrix.map((item, index) => (
                  <div key={item.name} className="flex items-center space-x-2">
                    <div className="w-3 h-3 rounded-full" style={{ backgroundColor: item.color }}></div>
                    <span className="text-white text-sm">{item.name}</span>
                  </div>
                ))}
              </div>
            </div>

            {/* План реализации */}
            <div className="bg-gradient-to-br from-orange-500/20 to-orange-600/10 backdrop-blur-sm rounded-xl p-6 border border-orange-500/30">
              <h2 className="text-2xl font-bold text-white mb-6">
                ⚡ План реализации
              </h2>
              <div className="space-y-4">
                {[
                  { phase: 'Этап 1', duration: '1-2 недели', items: ['CTA кнопки', 'Контактные формы'], color: '#FF6B6B', progress: 100 },
                  { phase: 'Этап 2', duration: '3-4 недели', items: ['Кейсы успеха', 'Отзывы клиентов'], color: '#4ECDC4', progress: 75 },
                  { phase: 'Этап 3', duration: '2 месяц', items: ['Редизайн сайта', 'Аналитика'], color: '#45B7D1', progress: 50 },
                  { phase: 'Этап 4', duration: '3 месяц', items: ['SEO продвижение', 'CRM система'], color: '#F7DC6F', progress: 25 }
                ].map((phase, index) => (
                  <div key={phase.phase} className="bg-white/10 rounded-lg p-4">
                    <div className="flex justify-between items-center mb-2">
                      <h3 className="font-bold text-white">{phase.phase}</h3>
                      <span className="text-gray-300 text-sm">{phase.duration}</span>
                    </div>
                    <div className="flex flex-wrap gap-2 mb-3">
                      {phase.items.map((item, i) => (
                        <span key={i} className="bg-white/20 text-white px-2 py-1 rounded text-sm">
                          {item}
                        </span>
                      ))}
                    </div>
                    <div className="w-full bg-gray-700 rounded-full h-2">
                      <div 
                        className="h-2 rounded-full transition-all duration-500"
                        style={{ backgroundColor: phase.color, width: `${phase.progress}%` }}
                      />
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {/* Итоговые рекомендации */}
        <div className="mt-8 bg-gradient-to-r from-indigo-500/20 to-purple-600/20 backdrop-blur-sm rounded-xl p-8 border border-indigo-500/30">
          <h2 className="text-3xl font-bold text-white mb-6 text-center">
            🎯 Ключевые выводы и рекомендации
          </h2>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div className="text-center">
              <div className="text-4xl font-bold text-green-400 mb-2">+580%</div>
              <p className="text-white">Прогнозируемый рост продаж через год</p>
            </div>
            <div className="text-center">
              <div className="text-4xl font-bold text-blue-400 mb-2">2-3 мес</div>
              <p className="text-white">Срок окупаемости инвестиций</p>
            </div>
            <div className="text-center">
              <div className="text-4xl font-bold text-purple-400 mb-2">320%</div>
              <p className="text-white">ROI при полной реализации</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  );
};

export default ConversionAnalysisDashboard;