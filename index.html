import { useState, useEffect, useMemo } from "react";

// ── PALETTE ─────────────────────────────────────────────────────────────────
const C = {
  bg:    '#080808',
  s1:    '#0F0F0F',
  s2:    '#171717',
  s3:    '#202020',
  bd:    '#2C2C2C',
  tx:    '#F0F0F0',
  mu:    '#545454',
  mu2:   '#888888',
  ac:    '#BAFF29',   // acid green = money
  acDim: 'rgba(186,255,41,0.1)',
  da:    '#FF3E3E',
  or:    '#FF8C00',
  bl:    '#3D8EFF',
  pu:    '#BB77FF',
};
const FH = "'Barlow Condensed', 'Arial Narrow', sans-serif";
const FM = "'JetBrains Mono', 'Courier New', monospace";

// ── CONSTANTS ────────────────────────────────────────────────────────────────
const CAT_META = {
  originals:   { label: 'Originals',    icon: '🎨' },
  prints:      { label: 'Prints',       icon: '🖼️' },
  commissions: { label: 'Commissions',  icon: '✏️' },
  digital:     { label: 'Digital',      icon: '💻' },
  other:       { label: 'Other',        icon: '📦' },
};

const STAGES = [
  { id: 'found',        label: '🔍 Found',       color: C.mu2 },
  { id: 'contacted',   label: '📩 Contacted',    color: C.bl  },
  { id: 'conversation',label: '💬 In Convo',     color: C.or  },
  { id: 'negotiating', label: '🤝 Negotiating',  color: C.pu  },
  { id: 'confirmed',   label: '💰 Confirmed',    color: C.ac  },
  { id: 'rejected',    label: '❌ Dead',          color: C.da  },
];

const OPP_TYPES = ['Shop','Wall','Gallery','Event','Other'];

const TABS = [
  { id: 'dashboard', label: 'Board',    icon: '⚡' },
  { id: 'income',    label: 'Income',   icon: '💵' },
  { id: 'roi',       label: 'ROI',      icon: '📊' },
  { id: 'pipeline',  label: 'Pipeline', icon: '🎯' },
  { id: 'goals',     label: 'Goals',    icon: '🏁' },
];

const DEFAULT_ACTIONS = [
  'Post 1 product online',
  'Message 3 potential buyers',
  'Add 2 new pipeline leads',
  'Follow up with 3 leads',
  'List 1 item on Etsy / Gumroad',
  'DM 1 shop about consignment',
];

// ── UTILS ────────────────────────────────────────────────────────────────────
const uid = () => Math.random().toString(36).slice(2, 9);
const today = () => new Date().toISOString().slice(0, 10);
const thisMonth = () => new Date().toISOString().slice(0, 7);
const monthLabel = () => new Date().toLocaleString('default', { month: 'long', year: 'numeric' });

const fmt = n => {
  const v = Number(n || 0);
  return '$' + v.toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
};
const fmtShort = n => {
  const v = Number(n || 0);
  if (v >= 1000) return '$' + (v / 1000).toFixed(1) + 'k';
  return '$' + Math.round(v);
};

const sumBy = (arr, key) => arr.reduce((s, e) => s + Number(e[key] || 0), 0);

const getMonthIncome = income => income.filter(e => (e.date || '').startsWith(thisMonth()));

const catTotals = income => Object.keys(CAT_META).map(id => ({
  id, label: CAT_META[id].icon + ' ' + CAT_META[id].label,
  total: sumBy(income.filter(e => e.cat === id), 'amount'),
})).sort((a, b) => b.total - a.total);

// ── BASE UI COMPONENTS ───────────────────────────────────────────────────────
const Btn = ({ children, onClick, variant = 'primary', size = 'md', disabled, sx = {} }) => {
  const [hover, setHover] = useState(false);
  const sizes = { sm: { padding: '5px 12px', fontSize: 11 }, md: { padding: '9px 18px', fontSize: 13 }, lg: { padding: '13px 26px', fontSize: 15 } };
  const variants = {
    primary:   { background: hover ? '#CCFF44' : C.ac, color: '#000' },
    secondary: { background: hover ? C.s3 : C.s2, color: C.tx, border: `1px solid ${C.bd}` },
    ghost:     { background: 'transparent', color: hover ? C.tx : C.mu, border: `1px solid ${hover ? C.bd : '#1A1A1A'}` },
    danger:    { background: hover ? '#FF5555' : C.da, color: '#fff' },
  };
  return (
    <button
      onClick={onClick}
      disabled={disabled}
      onMouseEnter={() => setHover(true)}
      onMouseLeave={() => setHover(false)}
      style={{
        fontFamily: FH, fontWeight: 700, letterSpacing: '0.06em', textTransform: 'uppercase',
        border: 'none', cursor: disabled ? 'not-allowed' : 'pointer',
        opacity: disabled ? 0.35 : 1, transition: 'all 0.1s', outline: 'none',
        ...sizes[size], ...variants[variant], ...sx,
      }}
    >{children}</button>
  );
};

const Inp = ({ label, value, onChange, type = 'text', placeholder, flex = 1, min }) => (
  <div style={{ display: 'flex', flexDirection: 'column', gap: 4, flex }}>
    {label && <span style={{ fontFamily: FH, fontSize: 10, fontWeight: 700, color: C.mu, letterSpacing: '0.1em', textTransform: 'uppercase' }}>{label}</span>}
    <input
      type={type} value={value} min={min}
      onChange={e => onChange(e.target.value)}
      placeholder={placeholder}
      style={{
        background: C.s2, border: `1px solid ${C.bd}`, color: C.tx,
        fontFamily: FM, fontSize: 13, padding: '8px 10px', outline: 'none',
        width: '100%', boxSizing: 'border-box',
      }}
    />
  </div>
);

const Sel = ({ label, value, onChange, options, flex = 1 }) => (
  <div style={{ display: 'flex', flexDirection: 'column', gap: 4, flex }}>
    {label && <span style={{ fontFamily: FH, fontSize: 10, fontWeight: 700, color: C.mu, letterSpacing: '0.1em', textTransform: 'uppercase' }}>{label}</span>}
    <select
      value={value} onChange={e => onChange(e.target.value)}
      style={{
        background: C.s2, border: `1px solid ${C.bd}`, color: C.tx,
        fontFamily: FM, fontSize: 13, padding: '8px 10px', outline: 'none',
        width: '100%', appearance: 'none', cursor: 'pointer',
      }}
    >
      {options.map(o => <option key={o.value} value={o.value}>{o.label}</option>)}
    </select>
  </div>
);

const Card = ({ children, sx = {} }) => (
  <div style={{ background: C.s1, border: `1px solid ${C.bd}`, padding: 16, ...sx }}>{children}</div>
);

const SectionLabel = ({ children }) => (
  <div style={{ fontFamily: FH, fontSize: 10, fontWeight: 700, color: C.mu, letterSpacing: '0.12em', textTransform: 'uppercase', marginBottom: 10 }}>{children}</div>
);

const XBtn = ({ onClick }) => (
  <button onClick={onClick} style={{ background: 'none', border: 'none', color: C.mu, cursor: 'pointer', fontSize: 16, padding: '0 4px', lineHeight: 1, flexShrink: 0 }}>×</button>
);

// ── BAR CHART ────────────────────────────────────────────────────────────────
const BarChart = ({ data }) => {
  const max = Math.max(...data.map(d => d.total), 1);
  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 9 }}>
      {data.map(d => (
        <div key={d.id} style={{ display: 'flex', alignItems: 'center', gap: 10 }}>
          <div style={{ fontFamily: FH, fontSize: 13, fontWeight: 600, color: d.total > 0 ? C.tx : C.mu, width: 120, flexShrink: 0 }}>{d.label}</div>
          <div style={{ flex: 1, background: C.s3, height: 5 }}>
            <div style={{ height: '100%', width: `${(d.total / max) * 100}%`, background: d.total > 0 ? C.ac : C.s3, transition: 'width 0.5s ease' }} />
          </div>
          <div style={{ fontFamily: FM, fontSize: 12, color: d.total > 0 ? C.ac : C.mu, width: 64, textAlign: 'right', flexShrink: 0 }}>{fmtShort(d.total)}</div>
        </div>
      ))}
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// TAB: DASHBOARD
// ─────────────────────────────────────────────────────────────────────────────
const Dashboard = ({ income, artworks, opps, monthGoal, onAiInsight, aiInsight, aiLoading }) => {
  const monthInc = getMonthIncome(income);
  const total = sumBy(monthInc, 'amount');
  const pct = Math.min((total / (monthGoal || 1000)) * 100, 100);
  const cats = catTotals(monthInc);
  const topCats = cats.filter(c => c.total > 0).slice(0, 3);
  const deadCats = cats.filter(c => c.total === 0);

  const confirmedOpps = opps.filter(o => o.stage === 'confirmed');
  const activeOpps    = opps.filter(o => !['confirmed','rejected'].includes(o.stage));
  const confirmedVal  = sumBy(confirmedOpps, 'actualValue');
  const conversion    = opps.length > 0 ? Math.round((confirmedOpps.length / opps.length) * 100) : 0;

  const topArtwork = artworks.length > 0
    ? [...artworks].sort((a, b) => b.hourlyRate - a.hourlyRate)[0]
    : null;

  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 14 }}>

      {/* Monthly Goal */}
      <Card>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'flex-start', marginBottom: 14 }}>
          <div>
            <SectionLabel>{monthLabel()}</SectionLabel>
            <div style={{ fontFamily: FH, fontSize: 48, fontWeight: 900, color: C.ac, lineHeight: 1 }}>{fmtShort(total)}</div>
            <div style={{ fontFamily: FM, fontSize: 11, color: C.mu, marginTop: 4 }}>of {fmt(monthGoal)} goal</div>
          </div>
          <div style={{ textAlign: 'right' }}>
            <div style={{ fontFamily: FH, fontSize: 56, fontWeight: 900, color: pct >= 100 ? C.ac : C.tx, lineHeight: 1 }}>{Math.round(pct)}%</div>
            <div style={{ fontFamily: FM, fontSize: 10, color: pct >= 100 ? C.ac : C.mu, marginTop: 4 }}>
              {pct >= 100 ? '🎯 GOAL HIT' : `${fmt(monthGoal - total)} remaining`}
            </div>
          </div>
        </div>
        <div style={{ background: C.s3, height: 6, width: '100%' }}>
          <div style={{ height: '100%', width: `${pct}%`, background: pct >= 100 ? C.ac : C.bl, transition: 'width 0.6s ease' }} />
        </div>
      </Card>

      {/* Income by Source */}
      <Card>
        <SectionLabel>Income by Source — This Month</SectionLabel>
        {monthInc.length === 0
          ? <div style={{ fontFamily: FM, fontSize: 12, color: C.mu, padding: '12px 0' }}>No income logged yet. Hit Income tab to start.</div>
          : <BarChart data={cats} />
        }
      </Card>

      {/* Money Intel / AI */}
      <Card sx={{ border: `1px solid ${C.bd}` }}>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: 12 }}>
          <SectionLabel>⚡ Money Intel</SectionLabel>
          <Btn onClick={onAiInsight} size="sm" disabled={aiLoading || income.length === 0}>
            {aiLoading ? '⏳ Analyzing...' : '⚡ AI Analyze'}
          </Btn>
        </div>
        {aiInsight ? (
          <div style={{ fontFamily: FM, fontSize: 12, color: C.tx, lineHeight: 1.7, background: C.acDim, border: `1px solid ${C.ac}33`, padding: 14, whiteSpace: 'pre-wrap' }}>
            {aiInsight}
          </div>
        ) : topCats.length > 0 ? (
          <div style={{ display: 'flex', flexDirection: 'column', gap: 8 }}>
            <div style={{ fontFamily: FH, fontSize: 14, fontWeight: 700, color: C.ac, letterSpacing: '0.03em' }}>
              ✅ DOUBLE DOWN → {topCats[0]?.label}
            </div>
            {deadCats.length > 0 && (
              <div style={{ fontFamily: FH, fontSize: 14, fontWeight: 700, color: C.da }}>
                🚫 DEAD WEIGHT → {deadCats.slice(0, 2).map(c => c.label).join(', ')}
              </div>
            )}
            <div style={{ fontFamily: FM, fontSize: 11, color: C.mu }}>Hit ⚡ AI Analyze for a real breakdown.</div>
          </div>
        ) : (
          <div style={{ fontFamily: FM, fontSize: 12, color: C.mu }}>Log income to unlock insights.</div>
        )}
      </Card>

      {/* Stats Row */}
      <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: 10 }}>
        {[
          { label: 'Active Leads',  value: activeOpps.length,    color: C.bl },
          { label: '% Conversion',  value: conversion + '%',     color: conversion > 30 ? C.ac : C.or },
          { label: 'Pipeline $',    value: fmtShort(confirmedVal + sumBy(activeOpps, 'estimatedValue')), color: C.ac },
        ].map(s => (
          <Card key={s.label} sx={{ textAlign: 'center', padding: 12 }}>
            <div style={{ fontFamily: FH, fontSize: 32, fontWeight: 900, color: s.color, lineHeight: 1 }}>{s.value}</div>
            <div style={{ fontFamily: FH, fontSize: 10, color: C.mu, textTransform: 'uppercase', letterSpacing: '0.08em', marginTop: 4 }}>{s.label}</div>
          </Card>
        ))}
      </div>

      {/* Top ROI */}
      {topArtwork && (
        <Card>
          <SectionLabel>Top ROI Artwork</SectionLabel>
          <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
            <div style={{ fontFamily: FH, fontSize: 18, fontWeight: 700, color: C.tx }}>{topArtwork.title}</div>
            <div style={{ fontFamily: FM, fontSize: 14, color: C.ac, fontWeight: 700 }}>{fmt(topArtwork.hourlyRate)}/hr</div>
          </div>
          <div style={{ fontFamily: FM, fontSize: 11, color: C.mu, marginTop: 4 }}>
            {fmt(topArtwork.profit)} profit · {topArtwork.hours}h work · sold for {fmt(topArtwork.salePrice)}
          </div>
        </Card>
      )}
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// TAB: INCOME
// ─────────────────────────────────────────────────────────────────────────────
const IncomeTab = ({ income, setIncome }) => {
  const [cat, setCat]       = useState('prints');
  const [amount, setAmount] = useState('');
  const [note, setNote]     = useState('');
  const [date, setDate]     = useState(today());

  const add = () => {
    const n = Number(amount);
    if (!n || n <= 0) return;
    setIncome(prev => [...prev, { id: uid(), cat, amount: n, note: note.trim(), date }]);
    setAmount(''); setNote('');
  };

  const monthInc  = getMonthIncome(income);
  const monthTotal = sumBy(monthInc, 'amount');
  const allCats    = catTotals(monthInc);

  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 14 }}>
      <Card>
        <SectionLabel>Log Income — Fast Entry</SectionLabel>
        <div style={{ display: 'flex', gap: 8, flexWrap: 'wrap', marginBottom: 10 }}>
          <Sel label="Category" value={cat} onChange={setCat} flex={2}
            options={Object.entries(CAT_META).map(([id, m]) => ({ value: id, label: m.icon + ' ' + m.label }))} />
          <Inp label="Amount $" value={amount} onChange={setAmount} type="number" placeholder="0.00" flex={1} />
          <Inp label="Date" value={date} onChange={setDate} type="date" flex={1} />
        </div>
        <div style={{ display: 'flex', gap: 8, alignItems: 'flex-end' }}>
          <Inp value={note} onChange={setNote} placeholder="Optional note (e.g. 'Print at Saturday market')" flex={1} label="Note" />
          <Btn onClick={add} sx={{ alignSelf: 'flex-end', flexShrink: 0 }}>+ Log</Btn>
        </div>
      </Card>

      {/* Month summary */}
      <Card>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
          <div>
            <SectionLabel>{monthLabel()}</SectionLabel>
            <div style={{ fontFamily: FH, fontSize: 42, fontWeight: 900, color: C.ac, lineHeight: 1 }}>{fmt(monthTotal)}</div>
          </div>
          <div style={{ fontFamily: FM, fontSize: 11, color: C.mu, textAlign: 'right' }}>
            {monthInc.length} entries<br/>avg {fmt(monthInc.length ? monthTotal / monthInc.length : 0)}
          </div>
        </div>
        {monthInc.length > 0 && (
          <div style={{ marginTop: 14 }}>
            <BarChart data={allCats} />
          </div>
        )}
      </Card>

      {/* Entry list */}
      <div>
        <SectionLabel>This Month's Entries</SectionLabel>
        {monthInc.length === 0 ? (
          <div style={{ fontFamily: FM, fontSize: 12, color: C.mu, padding: '24px 0', textAlign: 'center' }}>
            Nothing logged yet. Every dollar counts.
          </div>
        ) : (
          <div style={{ display: 'flex', flexDirection: 'column', gap: 6 }}>
            {[...monthInc].reverse().map(e => (
              <div key={e.id} style={{ display: 'flex', alignItems: 'center', background: C.s1, border: `1px solid ${C.bd}`, padding: '10px 14px', gap: 12 }}>
                <div style={{ fontSize: 20, flexShrink: 0 }}>{CAT_META[e.cat]?.icon || '📦'}</div>
                <div style={{ flex: 1, minWidth: 0 }}>
                  <div style={{ fontFamily: FH, fontSize: 14, fontWeight: 600, color: C.tx }}>{CAT_META[e.cat]?.label}</div>
                  {e.note && <div style={{ fontFamily: FM, fontSize: 11, color: C.mu, overflow: 'hidden', textOverflow: 'ellipsis', whiteSpace: 'nowrap' }}>{e.note}</div>}
                  <div style={{ fontFamily: FM, fontSize: 10, color: C.mu }}>{e.date}</div>
                </div>
                <div style={{ fontFamily: FM, fontSize: 16, fontWeight: 700, color: C.ac, flexShrink: 0 }}>{fmt(e.amount)}</div>
                <XBtn onClick={() => setIncome(prev => prev.filter(x => x.id !== e.id))} />
              </div>
            ))}
          </div>
        )}
      </div>
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// TAB: ROI TRACKER
// ─────────────────────────────────────────────────────────────────────────────
const ROITab = ({ artworks, setArtworks }) => {
  const [title, setTitle]       = useState('');
  const [hours, setHours]       = useState('');
  const [materials, setMats]    = useState('');
  const [salePrice, setSale]    = useState('');
  const [showForm, setShowForm] = useState(true);

  const add = () => {
    if (!title.trim() || !salePrice) return;
    const h  = Number(hours) || 0;
    const m  = Number(materials) || 0;
    const sp = Number(salePrice) || 0;
    const profit = sp - m;
    const hourlyRate = h > 0 ? profit / h : profit;
    setArtworks(prev => [...prev, { id: uid(), title: title.trim(), hours: h, materials: m, salePrice: sp, profit, hourlyRate, date: today() }]);
    setTitle(''); setHours(''); setMats(''); setSale('');
  };

  const sorted = useMemo(() => [...artworks].sort((a, b) => b.hourlyRate - a.hourlyRate), [artworks]);
  const bestHr = sorted[0]?.hourlyRate || 0;

  const totalProfit  = sumBy(artworks, 'profit');
  const totalRevenue = sumBy(artworks, 'salePrice');

  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 14 }}>
      {/* Stats */}
      {artworks.length > 0 && (
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: 10 }}>
          {[
            { label: 'Total Revenue', value: fmtShort(totalRevenue), color: C.tx },
            { label: 'Total Profit',  value: fmtShort(totalProfit),  color: C.ac },
            { label: 'Best $/hr',     value: fmtShort(bestHr),       color: C.or },
          ].map(s => (
            <Card key={s.label} sx={{ textAlign: 'center', padding: 12 }}>
              <div style={{ fontFamily: FH, fontSize: 28, fontWeight: 900, color: s.color, lineHeight: 1 }}>{s.value}</div>
              <div style={{ fontFamily: FH, fontSize: 10, color: C.mu, textTransform: 'uppercase', letterSpacing: '0.08em', marginTop: 4 }}>{s.label}</div>
            </Card>
          ))}
        </div>
      )}

      {/* Add Form */}
      <Card>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: showForm ? 12 : 0 }}>
          <SectionLabel>Add Artwork</SectionLabel>
          <Btn size="sm" variant="ghost" onClick={() => setShowForm(s => !s)}>{showForm ? '▲ Hide' : '▼ Show'}</Btn>
        </div>
        {showForm && (
          <>
            <div style={{ display: 'flex', gap: 8, flexWrap: 'wrap', marginBottom: 10 }}>
              <Inp label="Title" value={title} onChange={setTitle} placeholder="Artwork name" flex={3} />
              <Inp label="Hours" value={hours} onChange={setHours} type="number" placeholder="0" flex={1} min="0" />
              <Inp label="Materials $" value={materials} onChange={setMats} type="number" placeholder="0.00" flex={1} />
              <Inp label="Sale Price $" value={salePrice} onChange={setSale} type="number" placeholder="0.00" flex={1} />
            </div>
            <Btn onClick={add}>+ Add Artwork</Btn>
          </>
        )}
      </Card>

      {/* Ranking Table */}
      {artworks.length === 0 ? (
        <div style={{ fontFamily: FM, fontSize: 12, color: C.mu, textAlign: 'center', padding: 32 }}>
          Track artwork to find out what's actually worth your time.
        </div>
      ) : (
        <Card>
          <SectionLabel>Ranked by Hourly Rate</SectionLabel>
          {/* Header */}
          <div style={{ display: 'grid', gridTemplateColumns: '1fr 68px 68px 72px 72px 28px', gap: 6, paddingBottom: 8, borderBottom: `1px solid ${C.bd}` }}>
            {['Artwork','Sale','Cost','Profit','$/hr',''].map(h => (
              <div key={h} style={{ fontFamily: FH, fontSize: 9, fontWeight: 700, color: C.mu, textTransform: 'uppercase', letterSpacing: '0.1em' }}>{h}</div>
            ))}
          </div>
          {sorted.map((a, i) => (
            <div key={a.id} style={{ display: 'grid', gridTemplateColumns: '1fr 68px 68px 72px 72px 28px', gap: 6, padding: '10px 0', borderBottom: `1px solid ${C.s3}`, alignItems: 'center' }}>
              <div>
                <div style={{ fontFamily: FH, fontSize: 14, fontWeight: 700, color: i === 0 ? C.ac : C.tx }}>
                  {i === 0 && '🏆 '}{a.title}
                </div>
                <div style={{ fontFamily: FM, fontSize: 10, color: C.mu }}>{a.hours}h · {a.date}</div>
              </div>
              <div style={{ fontFamily: FM, fontSize: 12, color: C.tx }}>{fmt(a.salePrice)}</div>
              <div style={{ fontFamily: FM, fontSize: 12, color: a.materials > 0 ? C.da : C.mu }}>{a.materials > 0 ? fmt(a.materials) : '—'}</div>
              <div style={{ fontFamily: FM, fontSize: 12, fontWeight: 700, color: a.profit > 0 ? C.ac : C.da }}>{fmt(a.profit)}</div>
              <div style={{ fontFamily: FM, fontSize: 12, color: a.hourlyRate >= 25 ? C.ac : a.hourlyRate >= 10 ? C.or : C.da }}>
                {a.hours > 0 ? fmt(a.hourlyRate) : '—'}
              </div>
              <XBtn onClick={() => setArtworks(prev => prev.filter(x => x.id !== a.id))} />
            </div>
          ))}
        </Card>
      )}
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// TAB: PIPELINE
// ─────────────────────────────────────────────────────────────────────────────
const PipelineTab = ({ opps, setOpps }) => {
  const [showAdd, setShowAdd] = useState(false);
  const [view, setView]       = useState('kanban');
  const [name, setName]       = useState('');
  const [type, setType]       = useState('Shop');
  const [city, setCity]       = useState('');
  const [contact, setContact] = useState('');
  const [estVal, setEstVal]   = useState('');
  const [notes, setNotes]     = useState('');

  const add = () => {
    if (!name.trim()) return;
    setOpps(prev => [...prev, {
      id: uid(), name: name.trim(), type, city: city.trim(),
      contact: contact.trim(), estimatedValue: Number(estVal) || 0,
      actualValue: 0, notes: notes.trim(), stage: 'found', dateAdded: today(),
    }]);
    setName(''); setType('Shop'); setCity(''); setContact(''); setEstVal(''); setNotes('');
    setShowAdd(false);
  };

  const moveStage = (id, dir) => {
    const ids = STAGES.map(s => s.id);
    setOpps(prev => prev.map(o => {
      if (o.id !== id) return o;
      const next = ids[Math.max(0, Math.min(ids.length - 1, ids.indexOf(o.stage) + dir))];
      return { ...o, stage: next };
    }));
  };

  const stageGroups = STAGES.map(s => ({ ...s, items: opps.filter(o => o.stage === s.id) }));
  const kanbanCols  = stageGroups.filter(s => s.id !== 'rejected');
  const rejectedGrp = stageGroups.find(s => s.id === 'rejected');

  const totalEst      = sumBy(opps.filter(o => !['rejected'].includes(o.stage)), 'estimatedValue');
  const confirmedEst  = sumBy(opps.filter(o => o.stage === 'confirmed'), 'actualValue');
  const contactRate   = opps.length > 0 ? Math.round((opps.filter(o => o.stage !== 'found').length / opps.length) * 100) : 0;

  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 14 }}>
      {/* Header row */}
      <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center' }}>
        <div style={{ fontFamily: FH, fontSize: 20, fontWeight: 900, color: C.tx }}>{opps.length} Leads · {fmtShort(totalEst)} pipeline</div>
        <div style={{ display: 'flex', gap: 6 }}>
          <Btn size="sm" variant={view === 'kanban' ? 'primary' : 'ghost'} onClick={() => setView('kanban')}>Board</Btn>
          <Btn size="sm" variant={view === 'list' ? 'primary' : 'ghost'} onClick={() => setView('list')}>List</Btn>
          <Btn size="sm" onClick={() => setShowAdd(s => !s)}>+ Add</Btn>
        </div>
      </div>

      {/* Stats */}
      {opps.length > 0 && (
        <div style={{ display: 'grid', gridTemplateColumns: 'repeat(3, 1fr)', gap: 10 }}>
          {[
            { label: 'Total Leads',  value: opps.length,                              color: C.tx },
            { label: 'Contacted %',  value: contactRate + '%',                        color: C.bl },
            { label: 'Confirmed $',  value: fmtShort(confirmedEst || totalEst * 0.3), color: C.ac },
          ].map(s => (
            <Card key={s.label} sx={{ textAlign: 'center', padding: 10 }}>
              <div style={{ fontFamily: FH, fontSize: 26, fontWeight: 900, color: s.color, lineHeight: 1 }}>{s.value}</div>
              <div style={{ fontFamily: FH, fontSize: 9, color: C.mu, textTransform: 'uppercase', letterSpacing: '0.1em', marginTop: 3 }}>{s.label}</div>
            </Card>
          ))}
        </div>
      )}

      {/* Add Form */}
      {showAdd && (
        <Card>
          <SectionLabel>New Opportunity</SectionLabel>
          <div style={{ display: 'flex', gap: 8, flexWrap: 'wrap', marginBottom: 10 }}>
            <Inp label="Name" value={name} onChange={setName} placeholder="Shop / Wall / Gallery name" flex={3} />
            <Sel label="Type" value={type} onChange={setType} options={OPP_TYPES.map(t => ({ value: t, label: t }))} flex={1} />
          </div>
          <div style={{ display: 'flex', gap: 8, flexWrap: 'wrap', marginBottom: 10 }}>
            <Inp label="City" value={city} onChange={setCity} placeholder="e.g. Portland" flex={2} />
            <Inp label="Contact" value={contact} onChange={setContact} placeholder="Owner name / IG handle" flex={2} />
            <Inp label="Est. Value $" value={estVal} onChange={setEstVal} type="number" placeholder="0" flex={1} />
          </div>
          <div style={{ display: 'flex', gap: 8, alignItems: 'flex-end' }}>
            <Inp label="Notes" value={notes} onChange={setNotes} placeholder="e.g. Likes skulls, prefers bold color work" flex={1} />
            <Btn onClick={add} sx={{ flexShrink: 0, alignSelf: 'flex-end' }}>Add Lead</Btn>
          </div>
        </Card>
      )}

      {/* KANBAN BOARD */}
      {view === 'kanban' && (
        <div style={{ overflowX: 'auto', paddingBottom: 8 }}>
          <div style={{ display: 'flex', gap: 10, minWidth: 860 }}>
            {kanbanCols.map(sg => (
              <div key={sg.id} style={{ width: 158, flexShrink: 0 }}>
                <div style={{
                  fontFamily: FH, fontSize: 11, fontWeight: 800, color: sg.color,
                  letterSpacing: '0.07em', textTransform: 'uppercase',
                  borderBottom: `2px solid ${sg.color}`, paddingBottom: 6, marginBottom: 8,
                }}>
                  {sg.label} <span style={{ color: C.mu }}>({sg.items.length})</span>
                </div>
                <div style={{ display: 'flex', flexDirection: 'column', gap: 8 }}>
                  {sg.items.map(o => (
                    <div key={o.id} style={{ background: C.s1, border: `1px solid ${C.bd}`, padding: 10 }}>
                      <div style={{ fontFamily: FH, fontSize: 13, fontWeight: 700, color: sg.id === 'confirmed' ? C.ac : C.tx, marginBottom: 2 }}>{o.name}</div>
                      <div style={{ fontFamily: FM, fontSize: 10, color: C.mu, marginBottom: 4 }}>{o.type}{o.city ? ` · ${o.city}` : ''}</div>
                      {o.contact && <div style={{ fontFamily: FM, fontSize: 10, color: C.mu2, marginBottom: 4 }}>@{o.contact}</div>}
                      {o.estimatedValue > 0 && (
                        <div style={{ fontFamily: FM, fontSize: 11, color: C.or }}>{fmt(o.estimatedValue)} est.</div>
                      )}
                      {o.notes && (
                        <div style={{ fontFamily: FM, fontSize: 9, color: C.mu, lineHeight: 1.4, marginTop: 4, borderTop: `1px solid ${C.bd}`, paddingTop: 4 }}>
                          {o.notes.length > 70 ? o.notes.slice(0, 70) + '…' : o.notes}
                        </div>
                      )}
                      <div style={{ display: 'flex', gap: 4, marginTop: 8 }}>
                        <button onClick={() => moveStage(o.id, -1)} style={{ background: C.s3, border: 'none', color: C.mu, cursor: 'pointer', padding: '3px 7px', fontSize: 10, fontFamily: FH }}>◀</button>
                        <button onClick={() => moveStage(o.id, 1)} style={{ background: sg.id === 'negotiating' ? C.acDim : C.s3, border: `1px solid ${sg.id === 'negotiating' ? C.ac + '44' : C.bd}`, color: sg.id === 'negotiating' ? C.ac : C.mu, cursor: 'pointer', padding: '3px 7px', fontSize: 10, fontFamily: FH, flex: 1, fontWeight: 700 }}>▶ Next</button>
                        <button onClick={() => setOpps(prev => prev.filter(x => x.id !== o.id))} style={{ background: 'none', border: 'none', color: C.mu, cursor: 'pointer', fontSize: 13, padding: '0 4px' }}>×</button>
                      </div>
                    </div>
                  ))}
                  {sg.items.length === 0 && (
                    <div style={{ fontFamily: FM, fontSize: 10, color: '#1A1A1A', textAlign: 'center', padding: '14px 0', border: `1px dashed ${C.bd}` }}>—</div>
                  )}
                </div>
              </div>
            ))}
            {/* Rejected column (collapsed) */}
            <div style={{ width: 80, flexShrink: 0 }}>
              <div style={{ fontFamily: FH, fontSize: 9, fontWeight: 800, color: C.da, letterSpacing: '0.07em', textTransform: 'uppercase', borderBottom: `2px solid ${C.da}`, paddingBottom: 6, marginBottom: 8 }}>
                ❌ Dead ({rejectedGrp?.items.length || 0})
              </div>
              {rejectedGrp?.items.map(o => (
                <div key={o.id} style={{ background: C.s1, border: `1px solid #2A1111`, padding: 8, marginBottom: 6 }}>
                  <div style={{ fontFamily: FH, fontSize: 11, color: C.mu }}>{o.name.slice(0, 18)}{o.name.length > 18 ? '…' : ''}</div>
                  <button onClick={() => moveStage(o.id, -1)} style={{ background: C.s3, border: 'none', color: C.mu, cursor: 'pointer', padding: '2px 6px', fontSize: 9, marginTop: 4, fontFamily: FH }}>Revive</button>
                </div>
              ))}
            </div>
          </div>
        </div>
      )}

      {/* LIST VIEW */}
      {view === 'list' && (
        <div style={{ display: 'flex', flexDirection: 'column', gap: 6 }}>
          {opps.length === 0 ? (
            <div style={{ fontFamily: FM, fontSize: 12, color: C.mu, textAlign: 'center', padding: 32 }}>
              No leads yet. More shots on goal = more money.
            </div>
          ) : (
            opps.map(o => {
              const stage = STAGES.find(s => s.id === o.stage);
              return (
                <div key={o.id} style={{ display: 'flex', alignItems: 'center', background: C.s1, border: `1px solid ${C.bd}`, padding: '10px 14px', gap: 12 }}>
                  <div style={{ flex: 1, minWidth: 0 }}>
                    <div style={{ display: 'flex', alignItems: 'center', gap: 8, flexWrap: 'wrap', marginBottom: 2 }}>
                      <span style={{ fontFamily: FH, fontSize: 14, fontWeight: 700, color: C.tx }}>{o.name}</span>
                      <span style={{ fontFamily: FH, fontSize: 10, fontWeight: 700, letterSpacing: '0.06em', textTransform: 'uppercase', padding: '2px 7px', background: (stage?.color || C.mu) + '22', color: stage?.color || C.mu, border: `1px solid ${(stage?.color || C.mu) + '44'}` }}>
                        {stage?.label}
                      </span>
                    </div>
                    <div style={{ fontFamily: FM, fontSize: 10, color: C.mu }}>
                      {o.type}{o.city ? ` · ${o.city}` : ''}{o.contact ? ` · ${o.contact}` : ''}
                    </div>
                    {o.notes && <div style={{ fontFamily: FM, fontSize: 10, color: C.mu, marginTop: 2 }}>{o.notes}</div>}
                  </div>
                  <div style={{ textAlign: 'right', flexShrink: 0 }}>
                    {o.estimatedValue > 0 && <div style={{ fontFamily: FM, fontSize: 12, color: C.or, marginBottom: 4 }}>{fmt(o.estimatedValue)}</div>}
                    <div style={{ display: 'flex', gap: 4 }}>
                      <button onClick={() => moveStage(o.id, -1)} style={{ background: C.s3, border: 'none', color: C.mu, cursor: 'pointer', padding: '3px 9px', fontSize: 11, fontFamily: FH }}>◀</button>
                      <button onClick={() => moveStage(o.id, 1)} style={{ background: C.s3, border: 'none', color: C.mu, cursor: 'pointer', padding: '3px 9px', fontSize: 11, fontFamily: FH }}>▶</button>
                      <XBtn onClick={() => setOpps(prev => prev.filter(x => x.id !== o.id))} />
                    </div>
                  </div>
                </div>
              );
            })
          )}
        </div>
      )}
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// TAB: GOALS
// ─────────────────────────────────────────────────────────────────────────────
const GoalsTab = ({ income, monthGoal, setMonthGoal }) => {
  const [dailyTarget, setDailyTarget] = useState('30');
  const [checked, setChecked]         = useState([]);
  const [actions, setActions]         = useState(DEFAULT_ACTIONS.slice(0, 5));
  const [custom, setCustom]           = useState('');

  const todayInc   = income.filter(e => e.date === today());
  const todayTotal = sumBy(todayInc, 'amount');
  const target     = Number(dailyTarget) || 30;
  const monthInc   = getMonthIncome(income);
  const monthTotal = sumBy(monthInc, 'amount');
  const pct        = Math.min((monthTotal / (monthGoal || 1000)) * 100, 100);
  const daysLeft   = (() => {
    const now = new Date(); const end = new Date(now.getFullYear(), now.getMonth() + 1, 0);
    return end.getDate() - now.getDate();
  })();
  const dailyNeeded = monthGoal > monthTotal && daysLeft > 0 ? (monthGoal - monthTotal) / daysLeft : 0;

  const toggle = a => setChecked(prev => prev.includes(a) ? prev.filter(x => x !== a) : [...prev, a]);

  const addCustom = () => {
    if (!custom.trim()) return;
    setActions(prev => [...prev, custom.trim()]);
    setCustom('');
  };

  return (
    <div style={{ display: 'flex', flexDirection: 'column', gap: 14 }}>
      {/* Goal settings */}
      <Card>
        <SectionLabel>Goal Settings</SectionLabel>
        <div style={{ display: 'flex', gap: 10, flexWrap: 'wrap' }}>
          <Inp label="Monthly Target $" value={monthGoal.toString()} onChange={v => setMonthGoal(Number(v) || 1000)} type="number" flex={1} />
          <Inp label="Daily Target $" value={dailyTarget} onChange={setDailyTarget} type="number" flex={1} />
        </div>
        {dailyNeeded > 0 && (
          <div style={{ fontFamily: FM, fontSize: 11, color: C.or, marginTop: 10 }}>
            ⚡ Need {fmt(dailyNeeded)}/day for the next {daysLeft} days to hit your goal.
          </div>
        )}
      </Card>

      {/* Monthly progress */}
      <Card>
        <SectionLabel>Monthly Progress</SectionLabel>
        <div style={{ display: 'flex', justifyContent: 'space-between', marginBottom: 10 }}>
          <div style={{ fontFamily: FH, fontSize: 36, fontWeight: 900, color: C.ac }}>{fmt(monthTotal)}</div>
          <div style={{ fontFamily: FH, fontSize: 36, fontWeight: 900, color: C.mu }}>{Math.round(pct)}%</div>
        </div>
        <div style={{ background: C.s3, height: 8 }}>
          <div style={{ height: '100%', width: `${pct}%`, background: pct >= 100 ? C.ac : C.bl, transition: 'width 0.5s' }} />
        </div>
      </Card>

      {/* Today */}
      <Card>
        <div style={{ display: 'flex', justifyContent: 'space-between', alignItems: 'center', marginBottom: 12 }}>
          <div>
            <SectionLabel>Today — {today()}</SectionLabel>
            <div style={{ fontFamily: FH, fontSize: 32, fontWeight: 900, color: todayTotal >= target ? C.ac : C.tx }}>{fmt(todayTotal)}</div>
            <div style={{ fontFamily: FM, fontSize: 10, color: C.mu }}>of {fmt(target)} daily target</div>
          </div>
          <div style={{ textAlign: 'center' }}>
            <div style={{ fontFamily: FH, fontSize: 40, fontWeight: 900, color: checked.length === actions.length && actions.length > 0 ? C.ac : C.tx, lineHeight: 1 }}>
              {checked.length}/{actions.length}
            </div>
            <div style={{ fontFamily: FH, fontSize: 10, color: C.mu, textTransform: 'uppercase', letterSpacing: '0.08em', marginTop: 3 }}>Done</div>
          </div>
        </div>
        <div style={{ background: C.s3, height: 4 }}>
          <div style={{ height: '100%', width: actions.length > 0 ? `${(checked.length / actions.length) * 100}%` : '0%', background: C.ac, transition: 'width 0.3s' }} />
        </div>
      </Card>

      {/* Action checklist */}
      <Card>
        <SectionLabel>Today's Actions</SectionLabel>
        <div style={{ display: 'flex', flexDirection: 'column', gap: 8, marginBottom: 12 }}>
          {actions.map((a, i) => {
            const done = checked.includes(a);
            return (
              <div
                key={i}
                onClick={() => toggle(a)}
                style={{
                  display: 'flex', alignItems: 'center', gap: 12, padding: '11px 14px',
                  background: done ? C.acDim : C.s2, border: `1px solid ${done ? C.ac + '55' : C.bd}`,
                  cursor: 'pointer', transition: 'all 0.12s',
                }}
              >
                <div style={{
                  width: 18, height: 18, border: `2px solid ${done ? C.ac : C.mu}`,
                  background: done ? C.ac : 'transparent', flexShrink: 0,
                  display: 'flex', alignItems: 'center', justifyContent: 'center',
                }}>
                  {done && <span style={{ color: '#000', fontSize: 11, fontWeight: 900, lineHeight: 1 }}>✓</span>}
                </div>
                <span style={{ fontFamily: FH, fontSize: 15, fontWeight: 600, color: done ? C.ac : C.tx, textDecoration: done ? 'line-through' : 'none' }}>
                  {a}
                </span>
                <XBtn onClick={(e) => { e.stopPropagation(); setActions(prev => prev.filter((_, j) => j !== i)); setChecked(prev => prev.filter(x => x !== a)); }} />
              </div>
            );
          })}
        </div>
        <div style={{ display: 'flex', gap: 8 }}>
          <Inp value={custom} onChange={setCustom} placeholder="Add custom action..." flex={1} />
          <Btn onClick={addCustom} size="sm" variant="secondary" sx={{ alignSelf: 'stretch' }}>+ Add</Btn>
        </div>
      </Card>

      {checked.length === actions.length && actions.length > 0 && (
        <Card sx={{ background: C.acDim, border: `2px solid ${C.ac}`, textAlign: 'center', padding: '20px 16px' }}>
          <div style={{ fontFamily: FH, fontSize: 28, fontWeight: 900, color: C.ac, letterSpacing: '0.03em' }}>
            🔥 ALL DONE. NOW GO GET PAID.
          </div>
        </Card>
      )}
    </div>
  );
};

// ─────────────────────────────────────────────────────────────────────────────
// ROOT APP
// ─────────────────────────────────────────────────────────────────────────────
export default function ArtistIncomeEngine() {
  const [tab, setTab]           = useState('dashboard');
  const [income, setIncome]     = useState([]);
  const [artworks, setArtworks] = useState([]);
  const [opps, setOpps]         = useState([]);
  const [monthGoal, setMonthGoal] = useState(1000);
  const [loaded, setLoaded]     = useState(false);
  const [aiInsight, setAiInsight] = useState('');
  const [aiLoading, setAiLoading] = useState(false);

  // Inject fonts
  useEffect(() => {
    if (!document.getElementById('aie-fonts')) {
      const l = document.createElement('link');
      l.id = 'aie-fonts';
      l.rel = 'stylesheet';
      l.href = 'https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;600;700;900&family=JetBrains+Mono:wght@400;700&display=swap';
      document.head.appendChild(l);
    }
  }, []);

  // Load from storage
  useEffect(() => {
    async function load() {
      try {
        const r = await window.storage.get('aie_v2');
        if (r) {
          const d = JSON.parse(r.value);
          if (d.income)    setIncome(d.income);
          if (d.artworks)  setArtworks(d.artworks);
          if (d.opps)      setOpps(d.opps);
          if (d.monthGoal) setMonthGoal(d.monthGoal);
        }
      } catch (e) {}
      setLoaded(true);
    }
    load();
  }, []);

  // Save on change
  useEffect(() => {
    if (!loaded) return;
    window.storage.set('aie_v2', JSON.stringify({ income, artworks, opps, monthGoal })).catch(() => {});
  }, [income, artworks, opps, monthGoal, loaded]);

  // AI Insight
  const handleAiInsight = async () => {
    if (aiLoading || income.length === 0) return;
    setAiLoading(true);
    setAiInsight('');
    try {
      const monthInc = getMonthIncome(income);
      const cats     = catTotals(monthInc);
      const total    = sumBy(monthInc, 'amount');
      const confirmedOpps = opps.filter(o => o.stage === 'confirmed').length;

      const prompt = `You are a brutally honest business advisor for an independent artist. No fluff. No generic advice. Data only.

Income this month by category: ${JSON.stringify(cats.map(c => ({ cat: c.id, earned: c.total })))}
Total earned: $${total.toFixed(2)} of $${monthGoal} goal
Pipeline: ${opps.length} leads, ${confirmedOpps} confirmed
Artworks tracked: ${artworks.length}

Write a tight 3-point breakdown (under 120 words total):
1. DOUBLE DOWN: What's making real money and why to push it harder.
2. CUT: What's wasting time with zero return.  
3. DO TODAY: One specific action that could directly generate income this week.

Be specific. Use their actual numbers. No bullet headers — just plain numbered text.`;

      const res  = await fetch('https://api.anthropic.com/v1/messages', {
        method: 'POST',
        headers: { 'Content-Type': 'application/json' },
        body: JSON.stringify({
          model: 'claude-sonnet-4-20250514',
          max_tokens: 1000,
          messages: [{ role: 'user', content: prompt }],
        }),
      });
      const data = await res.json();
      const text = (data.content || []).map(b => b.text || '').join('');
      setAiInsight(text || 'No analysis returned. Try again.');
    } catch (e) {
      setAiInsight('Analysis failed. Check connection and retry.');
    }
    setAiLoading(false);
  };

  const monthTotal = sumBy(getMonthIncome(income), 'amount');

  if (!loaded) {
    return (
      <div style={{ background: C.bg, height: '100vh', display: 'flex', alignItems: 'center', justifyContent: 'center', fontFamily: FM, fontSize: 14, color: C.mu }}>
        Loading system...
      </div>
    );
  }

  return (
    <div style={{ background: C.bg, minHeight: '100vh', color: C.tx, fontFamily: FH }}>
      {/* ── TOP NAV ── */}
      <div style={{ background: C.s1, borderBottom: `1px solid ${C.bd}`, padding: '10px 18px', display: 'flex', justifyContent: 'space-between', alignItems: 'center', position: 'sticky', top: 0, zIndex: 100 }}>
        <div>
          <div style={{ fontFamily: FH, fontSize: 20, fontWeight: 900, color: C.ac, letterSpacing: '0.04em', lineHeight: 1.1 }}>INCOME ENGINE</div>
          <div style={{ fontFamily: FM, fontSize: 9, color: C.mu, letterSpacing: '0.04em' }}>ARTIST FINANCIAL SYSTEM</div>
        </div>
        <div style={{ textAlign: 'right' }}>
          <div style={{ fontFamily: FM, fontSize: 18, fontWeight: 700, color: C.tx }}>{fmt(monthTotal)}</div>
          <div style={{ fontFamily: FM, fontSize: 9, color: C.mu }}>{monthLabel().toUpperCase()}</div>
        </div>
      </div>

      {/* ── TAB BAR ── */}
      <div style={{ background: C.s1, borderBottom: `1px solid ${C.bd}`, display: 'flex', overflowX: 'auto' }}>
        {TABS.map(t => (
          <button
            key={t.id}
            onClick={() => setTab(t.id)}
            style={{
              flex: 1, minWidth: 58, padding: '10px 6px', background: 'none', border: 'none',
              cursor: 'pointer', fontFamily: FH, fontSize: 11, fontWeight: tab === t.id ? 800 : 400,
              color: tab === t.id ? C.ac : C.mu, letterSpacing: '0.05em', textTransform: 'uppercase',
              borderBottom: `2px solid ${tab === t.id ? C.ac : 'transparent'}`, transition: 'all 0.12s',
              outline: 'none',
            }}
          >
            <div style={{ fontSize: 18, marginBottom: 2 }}>{t.icon}</div>
            {t.label}
          </button>
        ))}
      </div>

      {/* ── CONTENT ── */}
      <div style={{ padding: 16, paddingBottom: 48, maxWidth: 780, margin: '0 auto' }}>
        {tab === 'dashboard' && (
          <Dashboard income={income} artworks={artworks} opps={opps} monthGoal={monthGoal}
            onAiInsight={handleAiInsight} aiInsight={aiInsight} aiLoading={aiLoading} />
        )}
        {tab === 'income'    && <IncomeTab income={income} setIncome={setIncome} />}
        {tab === 'roi'       && <ROITab artworks={artworks} setArtworks={setArtworks} />}
        {tab === 'pipeline'  && <PipelineTab opps={opps} setOpps={setOpps} />}
        {tab === 'goals'     && <GoalsTab income={income} monthGoal={monthGoal} setMonthGoal={setMonthGoal} />}
      </div>
    </div>
  );
}
