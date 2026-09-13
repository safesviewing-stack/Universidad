import React, { useState, useMemo } from 'react';
import { Heart, Home, MapPin, Users, Wifi, Wind, Zap, Clock, TrendingUp, Search, ChevronDown, Star, MapPinned, AlertCircle, Check, Plus, Trash2, BarChart3, Menu, X } from 'lucide-react';

const UNIVERSITIES = {
  upv: { name: 'UPV', full: 'Universitat Politècnica de València', lat: 39.4799, lng: -0.3436, color: '#FF6B35' },
  uv: { name: 'UV', full: 'Universitat de València', lat: 39.4789, lng: -0.3844, color: '#004E89' },
  uev: { name: 'UEV', full: 'Universidad Europea de Valencia', lat: 39.4700, lng: -0.3500, color: '#7209B7' },
  ucv: { name: 'UCV', full: 'Universidad Católica de Valencia', lat: 39.4900, lng: -0.3600, color: '#F72585' },
  uiv: { name: 'UIV', full: 'Universidad Internacional de Valencia', lat: 39.4600, lng: -0.3400, color: '#06FFA5' },
};

const BARRIOS = [
  'Benimaclet', 'Algirós', 'Amistat', 'Mestalla', 'Ruzafa', 'Ciutat Vella',
  'Patraix', 'Campanar', 'Blasco Ibáñez', 'Ayora', 'Cabanyal', 'Camins al Grau'
];

const generateListings = () => {
  const listings = [];
  const types = ['Habitación individual', 'Habitación compartida', 'Piso completo'];
  const amenities = [
    { icon: 'wifi', label: 'WiFi' },
    { icon: 'wind', label: 'Aire acondicionado' },
    { icon: 'zap', label: 'Calefacción' },
    { icon: 'users', label: 'Piso compartido' },
  ];

  const barrioCoords = {
    'Benimaclet': [39.4850, -0.3250],
    'Algirós': [39.4780, -0.3100],
    'Amistat': [39.4900, -0.3900],
    'Mestalla': [39.4720, -0.3400],
    'Ruzafa': [39.4650, -0.3850],
    'Ciutat Vella': [39.4700, -0.3800],
    'Patraix': [39.4600, -0.3500],
    'Campanar': [39.4550, -0.3600],
    'Blasco Ibáñez': [39.4750, -0.3750],
    'Ayora': [39.4850, -0.3550],
    'Cabanyal': [39.4600, -0.3200],
    'Camins al Grau': [39.4550, -0.3300],
  };

  let id = 1;
  for (const barrio of BARRIOS) {
    const count = Math.floor(Math.random() * 4) + 2;
    for (let i = 0; i < count; i++) {
      const coords = barrioCoords[barrio];
      const lat = coords[0] + (Math.random() - 0.5) * 0.01;
      const lng = coords[1] + (Math.random() - 0.5) * 0.01;
      const price = Math.floor(Math.random() * 600) + 300;
      const rooms = Math.floor(Math.random() * 4) + 1;
      const type = types[Math.floor(Math.random() * types.length)];
      const selectedAmenities = amenities.slice(0, Math.floor(Math.random() * 3) + 2);
      const nearestUni = Object.keys(UNIVERSITIES)[Math.floor(Math.random() * Object.keys(UNIVERSITIES).length)];

      listings.push({
        id: id++,
        address: `${type} en ${barrio}`,
        price,
        rooms,
        type,
        barrio,
        latitude: lat,
        longitude: lng,
        amenities: selectedAmenities,
        rating: Math.floor(Math.random() * 40) + 75,
        nearestUni,
        images: [`🏠`, `🏘️`, `🏢`][Math.floor(Math.random() * 3)],
        furnished: Math.random() > 0.5,
        elevator: Math.random() > 0.5,
        terrace: Math.random() > 0.5,
        utilities: Math.random() > 0.5,
        minStay: Math.floor(Math.random() * 6) + 6,
        available: new Date(Date.now() + Math.random() * 90 * 24 * 60 * 60 * 1000).toLocaleDateString(),
      });
    }
  }
  return listings;
};

const calculateDistance = (lat1, lng1, lat2, lng2) => {
  const R = 6371;
  const dLat = (lat2 - lat1) * Math.PI / 180;
  const dLng = (lng2 - lng1) * Math.PI / 180;
  const a = Math.sin(dLat/2) * Math.sin(dLat/2) + Math.cos(lat1 * Math.PI / 180) * Math.cos(lat2 * Math.PI / 180) * Math.sin(dLng/2) * Math.sin(dLng/2);
  const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1-a));
  return R * c;
};

const estimateTime = (distance, transport) => {
  const speeds = { walk: 1.3, bike: 4, bus: 2.5, metro: 3 };
  const speed = speeds[transport] || 1.3;
  return Math.ceil((distance * 60) / speed);
};

export default function PisoCampus() {
  const [listings] = useState(generateListings());
  const [currentPage, setCurrentPage] = useState('home');
  const [selectedUniversity, setSelectedUniversity] = useState('upv');
  const [priceRange, setPriceRange] = useState([300, 1000]);
  const [maxTransport, setMaxTransport] = useState('bus');
  const [favorites, setFavorites] = useState(new Set());
  const [filters, setFilters] = useState({
    university: 'upv',
    maxPrice: 1000,
    minPrice: 300,
    type: 'all',
    furnished: 'all',
    amenities: [],
    barrio: 'all',
  });
  const [compared, setCompared] = useState(new Set());
  const [mobileMenuOpen, setMobileMenuOpen] = useState(false);

  const selectedUniData = UNIVERSITIES[selectedUniversity];

  const calculateScore = (listing) => {
    let score = 50;
    const distance = calculateDistance(selectedUniData.lat, selectedUniData.lng, listing.latitude, listing.longitude);
    const time = estimateTime(distance, maxTransport);

    score += Math.max(0, Math.min(20, 20 - (time / 2)));
    score += Math.max(0, Math.min(15, 15 - ((listing.price - 300) / 50)));
    score += listing.amenities.length * 2;
    score += listing.rating / 10;

    return Math.min(100, Math.round(score));
  };

  const filteredListings = useMemo(() => {
    return listings
      .filter(l => l.price >= filters.minPrice && l.price <= filters.maxPrice)
      .filter(l => filters.type === 'all' || l.type === filters.type)
      .filter(l => filters.barrio === 'all' || l.barrio === filters.barrio)
      .filter(l => filters.furnished === 'all' || l.furnished === (filters.furnished === 'yes'))
      .sort((a, b) => calculateScore(b) - calculateScore(a));
  }, [listings, filters]);

  const renderStars = (rating) => {
    const stars = Math.round(rating / 20);
    return '⭐'.repeat(stars) + '☆'.repeat(5 - stars);
  };

  const HomeView = () => (
    <div className="min-h-screen bg-white">
      <div className="bg-gradient-to-b from-orange-500 to-orange-400 text-white px-4 py-16 text-center">
        <div className="max-w-2xl mx-auto">
          <h1 className="text-4xl md:text-5xl font-bold mb-4">Encuentra piso.<br/>Vive cerca de tu universidad.</h1>
          <p className="text-lg opacity-90 mb-8">Compara alojamientos de Valencia según precio, ubicación y tiempo hasta tu universidad.</p>
        </div>
      </div>

      <div className="max-w-4xl mx-auto px-4 py-12 space-y-8">
        <div className="bg-white rounded-2xl shadow-sm border border-gray-100 p-8">
          <h2 className="text-xl font-bold text-gray-900 mb-6">¿Dónde estudias?</h2>
          <div className="grid grid-cols-2 md:grid-cols-3 gap-4 mb-8">
            {Object.entries(UNIVERSITIES).map(([key, uni]) => (
              <button
                key={key}
                onClick={() => setSelectedUniversity(key)}
                className={`p-4 rounded-lg border-2 transition-all font-semibold ${
                  selectedUniversity === key
                    ? 'border-orange-500 bg-orange-50 text-orange-700'
                    : 'border-gray-200 text-gray-600 hover:border-gray-300'
                }`}
              >
                {uni.name}
              </button>
            ))}
          </div>

          <h2 className="text-xl font-bold text-gray-900 mb-4">¿Cuánto quieres pagar?</h2>
          <div className="mb-6 space-y-2">
            <input
              type="range"
              min="300"
              max="1500"
              value={priceRange[1]}
              onChange={(e) => setPriceRange([priceRange[0], parseInt(e.target.value)])}
              className="w-full"
            />
            <p className="text-center text-lg font-semibold text-orange-600">
              {priceRange[0]}€ — {priceRange[1]}€/mes
            </p>
          </div>

          <h2 className="text-xl font-bold text-gray-900 mb-4">¿Cuánto quieres tardar?</h2>
          <div className="grid grid-cols-2 md:grid-cols-4 gap-3 mb-8">
            {[
              { icon: '🚶', label: '15 min', value: 'walk' },
              { icon: '🚲', label: '15 min', value: 'bike' },
              { icon: '🚌', label: '20 min', value: 'bus' },
              { icon: '🚇', label: '30 min', value: 'metro' },
            ].map((opt) => (
              <button
                key={opt.value}
                onClick={() => setMaxTransport(opt.value)}
                className={`p-3 rounded-lg border-2 transition-all flex items-center justify-center gap-2 font-semibold ${
                  maxTransport === opt.value
                    ? 'border-orange-500 bg-orange-50 text-orange-700'
                    : 'border-gray-200 text-gray-600'
                }`}
              >
                <span className="text-2xl">{opt.icon}</span>
              </button>
            ))}
          </div>

          <button
            onClick={() => {
              setFilters({...filters, university: selectedUniversity, maxPrice: priceRange[1], minPrice: priceRange[0]});
              setCurrentPage('search');
            }}
            className="w-full bg-orange-500 hover:bg-orange-600 text-white font-bold py-4 px-6 rounded-lg text-lg transition-colors"
          >
            BUSCAR PISO
          </button>
        </div>

        <div className="grid md:grid-cols-3 gap-6">
          {[
            { icon: '🎓', title: 'Para estudiantes', desc: 'Diseñado específicamente para tu estilo de vida' },
            { icon: '📍', title: 'Ubicación exacta', desc: 'Sabe cuánto tardas realmente hasta tu uni' },
            { icon: '⭐', title: 'Puntuación personal', desc: 'Cada piso adaptado a tus necesidades' },
          ].map((feature, i) => (
            <div key={i} className="bg-gradient-to-br from-blue-50 to-indigo-50 rounded-xl p-6 border border-blue-100">
              <div className="text-3xl mb-3">{feature.icon}</div>
              <h3 className="font-bold text-gray-900 mb-2">{feature.title}</h3>
              <p className="text-gray-600 text-sm">{feature.desc}</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  const SearchView = () => (
    <div className="min-h-screen bg-gray-50">
      <div className="bg-orange-500 text-white px-4 py-4 sticky top-0 z-10">
        <button onClick={() => setCurrentPage('home')} className="flex items-center gap-2 text-lg font-semibold">
          ← Volver
        </button>
      </div>

      <div className="max-w-7xl mx-auto px-4 py-8">
        <div className="grid md:grid-cols-4 gap-6">
          <div className="md:col-span-1 space-y-6">
            <div className="bg-white rounded-lg p-4 border border-gray-200">
              <h3 className="font-bold text-gray-900 mb-3">Filtros</h3>

              <div className="space-y-4">
                <div>
                  <label className="text-sm font-semibold text-gray-700">Universidad</label>
                  <select value={filters.university} onChange={(e) => setFilters({...filters, university: e.target.value})} className="w-full mt-1 p-2 border border-gray-200 rounded text-sm">
                    {Object.entries(UNIVERSITIES).map(([k, v]) => <option key={k} value={k}>{v.name}</option>)}
                  </select>
                </div>

                <div>
                  <label className="text-sm font-semibold text-gray-700">Precio máximo: {filters.maxPrice}€</label>
                  <input type="range" min="300" max="1500" value={filters.maxPrice} onChange={(e) => setFilters({...filters, maxPrice: parseInt(e.target.value)})} className="w-full mt-1" />
                </div>

                <div>
                  <label className="text-sm font-semibold text-gray-700">Tipo</label>
                  <select value={filters.type} onChange={(e) => setFilters({...filters, type: e.target.value})} className="w-full mt-1 p-2 border border-gray-200 rounded text-sm">
                    <option value="all">Todos</option>
                    <option value="Habitación individual">Habitación individual</option>
                    <option value="Habitación compartida">Habitación compartida</option>
                    <option value="Piso completo">Piso completo</option>
                  </select>
                </div>

                <div>
                  <label className="text-sm font-semibold text-gray-700">Barrio</label>
                  <select value={filters.barrio} onChange={(e) => setFilters({...filters, barrio: e.target.value})} className="w-full mt-1 p-2 border border-gray-200 rounded text-sm">
                    <option value="all">Todos</option>
                    {BARRIOS.map(b => <option key={b} value={b}>{b}</option>)}
                  </select>
                </div>

                <div>
                  <label className="text-sm font-semibold text-gray-700">Amueblado</label>
                  <select value={filters.furnished} onChange={(e) => setFilters({...filters, furnished: e.target.value})} className="w-full mt-1 p-2 border border-gray-200 rounded text-sm">
                    <option value="all">Indiferente</option>
                    <option value="yes">Sí</option>
                    <option value="no">No</option>
                  </select>
                </div>
              </div>
            </div>

            {compared.size > 0 && (
              <button onClick={() => setCurrentPage('compare')} className="w-full bg-indigo-500 hover:bg-indigo-600 text-white font-bold py-3 rounded-lg">
                Comparar ({compared.size})
              </button>
            )}
          </div>

          <div className="md:col-span-3 space-y-4">
            <p className="text-gray-600 font-semibold">{filteredListings.length} alojamientos encontrados</p>
            {filteredListings.map((listing) => {
              const distance = calculateDistance(UNIVERSITIES[filters.university].lat, UNIVERSITIES[filters.university].lng, listing.latitude, listing.longitude);
              const times = {
                walk: estimateTime(distance, 'walk'),
                bike: estimateTime(distance, 'bike'),
                bus: estimateTime(distance, 'bus'),
                metro: estimateTime(distance, 'metro'),
              };
              const score = calculateScore(listing);

              return (
                <div key={listing.id} className="bg-white rounded-xl border border-gray-200 overflow-hidden hover:shadow-lg transition-shadow">
                  <div className="flex flex-col md:flex-row">
                    <div className="md:w-48 h-40 bg-gradient-to-br from-orange-200 to-orange-100 flex items-center justify-center text-6xl flex-shrink-0">
                      {listing.images}
                    </div>
                    <div className="flex-1 p-6">
                      <div className="flex justify-between items-start mb-2">
                        <div>
                          <h3 className="text-lg font-bold text-gray-900">{listing.address}</h3>
                          <p className="text-sm text-gray-500">{listing.barrio}</p>
                        </div>
                        <div className="text-right">
                          <p className="text-2xl font-bold text-orange-600">{listing.price}€</p>
                          <p className="text-xs text-gray-500">/mes</p>
                        </div>
                      </div>

                      <div className="flex gap-4 my-3 text-sm text-gray-600">
                        <span>{listing.rooms} hab</span>
                        <span>•</span>
                        <span className="flex items-center gap-1">{listing.amenities.length > 0 && listing.amenities.map(a => a.label).join(', ')}</span>
                      </div>

                      <div className="bg-gray-50 rounded-lg p-3 my-3 text-sm">
                        <p className="font-semibold text-gray-900 mb-2">Tiempo hasta {UNIVERSITIES[filters.university].name}</p>
                        <div className="grid grid-cols-4 gap-2">
                          <div>🚶 {times.walk}m</div>
                          <div>🚲 {times.bike}m</div>
                          <div>🚌 {times.bus}m</div>
                          <div>🚇 {times.metro}m</div>
                        </div>
                      </div>

                      <div className="flex justify-between items-center">
                        <div className="flex items-center gap-2">
                          <span className="text-lg font-bold text-orange-600">⭐ {score}/100</span>
                          <span className="text-xs text-gray-500">para ti</span>
                        </div>
                        <div className="flex gap-2">
                          <button onClick={() => setCompared(prev => new Set(prev.has(listing.id) ? [...prev].filter(id => id !== listing.id) : [...prev, listing.id]))} className={`p-2 rounded-lg ${compared.has(listing.id) ? 'bg-indigo-100 text-indigo-600' : 'bg-gray-100 text-gray-600'}`}>
                            ⚖️
                          </button>
                          <button onClick={() => setFavorites(prev => new Set(prev.has(listing.id) ? [...prev].filter(id => id !== listing.id) : [...prev, listing.id]))} className={`p-2 rounded-lg ${favorites.has(listing.id) ? 'bg-red-100 text-red-600' : 'bg-gray-100 text-gray-600'}`}>
                            ❤️
                          </button>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              );
            })}
          </div>
        </div>
      </div>
    </div>
  );

  const FavoritesView = () => (
    <div className="min-h-screen bg-gray-50">
      <div className="bg-red-500 text-white px-4 py-4 sticky top-0 z-10">
        <button onClick={() => setCurrentPage('home')} className="flex items-center gap-2 text-lg font-semibold">
          ← Volver
        </button>
      </div>

      <div className="max-w-4xl mx-auto px-4 py-8">
        <h1 className="text-3xl font-bold text-gray-900 mb-8">Mis pisos favoritos ({favorites.size})</h1>
        {favorites.size === 0 ? (
          <div className="text-center py-16">
            <p className="text-gray-500 text-lg">No tienes favoritos guardados</p>
            <button onClick={() => setCurrentPage('search')} className="mt-4 bg-orange-500 hover:bg-orange-600 text-white font-bold py-2 px-6 rounded-lg">Buscar pisos</button>
          </div>
        ) : (
          <div className="space-y-4">
            {listings.filter(l => favorites.has(l.id)).map((listing) => (
              <div key={listing.id} className="bg-white rounded-lg p-4 border border-gray-200 flex justify-between items-center">
                <div>
                  <h3 className="font-bold text-gray-900">{listing.address}</h3>
                  <p className="text-orange-600 font-semibold">{listing.price}€/mes</p>
                </div>
                <button onClick={() => setFavorites(prev => new Set([...prev].filter(id => id !== listing.id)))} className="text-red-500 hover:text-red-700">
                  <Trash2 size={20} />
                </button>
              </div>
            ))}
          </div>
        )}
      </div>
    </div>
  );

  const CompareView = () => {
    const comparedListings = listings.filter(l => compared.has(l.id));
    
    return (
      <div className="min-h-screen bg-gray-50">
        <div className="bg-indigo-500 text-white px-4 py-4 sticky top-0 z-10">
          <button onClick={() => setCurrentPage('search')} className="flex items-center gap-2 text-lg font-semibold">
            ← Volver
          </button>
        </div>

        <div className="max-w-6xl mx-auto px-4 py-8">
          <h1 className="text-3xl font-bold text-gray-900 mb-8">Comparar pisos</h1>
          <div className="overflow-x-auto bg-white rounded-lg border border-gray-200">
            <table className="w-full text-sm">
              <thead>
                <tr className="border-b border-gray-200 bg-gray-50">
                  <th className="p-4 text-left font-bold text-gray-900">Característica</th>
                  {comparedListings.slice(0, 3).map((l) => (
                    <th key={l.id} className="p-4 text-center font-bold text-gray-900">{l.address}</th>
                  ))}
                </tr>
              </thead>
              <tbody>
                <tr className="border-b border-gray-200">
                  <td className="p-4 font-semibold text-gray-900">Precio</td>
                  {comparedListings.slice(0, 3).map((l) => (
                    <td key={l.id} className="p-4 text-center font-bold text-orange-600">{l.price}€</td>
                  ))}
                </tr>
                <tr className="border-b border-gray-200">
                  <td className="p-4 font-semibold text-gray-900">Habitaciones</td>
                  {comparedListings.slice(0, 3).map((l) => (
                    <td key={l.id} className="p-4 text-center">{l.rooms}</td>
                  ))}
                </tr>
                <tr className="border-b border-gray-200">
                  <td className="p-4 font-semibold text-gray-900">Tipo</td>
                  {comparedListings.slice(0, 3).map((l) => (
                    <td key={l.id} className="p-4 text-center text-sm">{l.type}</td>
                  ))}
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    );
  };

  const StatsView = () => (
    <div className="min-h-screen bg-gradient-to-b from-purple-50 to-white">
      <div className="bg-purple-500 text-white px-4 py-4 sticky top-0 z-10">
        <button onClick={() => setCurrentPage('home')} className="flex items-center gap-2 text-lg font-semibold">
          ← Volver
        </button>
      </div>

      <div className="max-w-4xl mx-auto px-4 py-12">
        <h1 className="text-3xl font-bold text-gray-900 mb-12 text-center">Valencia para estudiantes</h1>
        
        <div className="grid md:grid-cols-2 gap-6">
          {[
            { icon: '💰', title: 'Precio medio', value: '450€', desc: 'Habitación/mes' },
            { icon: '🏘️', title: 'Barrio popular', value: 'Benimaclet', desc: 'Más pisos listados' },
            { icon: '🎓', title: 'Más cercana', value: 'UPV', desc: 'En promedio' },
            { icon: '⏱️', title: 'Tiempo promedio', value: '18 min', desc: 'A la universidad' },
          ].map((stat, i) => (
            <div key={i} className="bg-white rounded-xl p-6 border border-gray-200 text-center">
              <div className="text-4xl mb-3">{stat.icon}</div>
              <p className="text-gray-600 text-sm mb-2">{stat.title}</p>
              <p className="text-3xl font-bold text-purple-600">{stat.value}</p>
              <p className="text-xs text-gray-500 mt-2">{stat.desc}</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );

  return (
    <div className="bg-white">
      {currentPage === 'home' && <HomeView />}
      {currentPage === 'search' && <SearchView />}
      {currentPage === 'favorites' && <FavoritesView />}
      {currentPage === 'compare' && <CompareView />}
      {currentPage === 'stats' && <StatsView />}

      <nav className="fixed bottom-0 md:top-0 left-0 right-0 bg-white border-t md:border-t-0 md:border-b border-gray-200 md:sticky md:z-20">
        <div className="flex justify-around md:justify-start gap-4 px-4 py-3 max-w-4xl mx-auto">
          {[
            { id: 'home', icon: '🏠', label: 'Inicio' },
            { id: 'search', icon: '🔎', label: 'Buscar' },
            { id: 'stats', icon: '📊', label: 'Datos' },
            { id: 'favorites', icon: '❤️', label: 'Favoritos' },
          ].map((item) => (
            <button
              key={item.id}
              onClick={() => setCurrentPage(item.id)}
              className={`flex flex-col items-center gap-1 px-4 py-2 rounded-lg transition-colors ${
                currentPage === item.id
                  ? 'text-orange-600 bg-orange-50'
                  : 'text-gray-600 hover:text-orange-600'
              }`}
            >
              <span className="text-2xl">{item.icon}</span>
              <span className="text-xs font-semibold">{item.label}</span>
            </button>
          ))}
        </div>
      </nav>

      <div className="h-20 md:h-0"></div>
    </div>
  );
}
