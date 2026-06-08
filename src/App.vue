<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="#" aria-label="RIC Beijing home">
        <span class="brand-logo-wrap">
          <img class="brand-logo" src="./assets/wmo-logo.png" alt="WMO emblem" />
        </span>
        <span>
          <strong>RIC Beijing</strong>
          <small>Regional Instrument Center of RA II</small>
        </span>
      </a>

      <button class="menu-toggle" type="button" @click="isMenuOpen = !isMenuOpen">
        <MenuIcon />
        <span>Menu</span>
      </button>

      <nav :class="['primary-nav', { 'is-open': isMenuOpen }]" aria-label="Primary navigation">
        <a v-for="item in navItems" :key="item" href="#">{{ item }}</a>
        <button class="language" type="button">
          <GlobeIcon />
          EN
          <ChevronDownIcon />
        </button>
      </nav>
    </header>

    <main>
      <section class="hero">
        <div class="hero-overlay"></div>
        <div class="hero-content">
          <p class="eyebrow">RIC Beijing</p>
          <h1>RIC Beijing Regional Instrument Center of RA II</h1>
          <p class="hero-copy">
            Traceable calibration, comparison and technical support for
            meteorological observations across WMO Region II and beyond.
          </p>
          <div class="hero-actions">
            <a class="button button-primary" href="#">
              <CalendarIcon />
              Request Calibration Service
            </a>
            <a class="button button-secondary" href="#">
              <ChartIcon />
              View Capabilities
            </a>
          </div>
        </div>
        <aside class="hero-note" aria-label="Service highlight">
          <TargetIcon />
          <div>
            <strong>Supporting reliable observations</strong>
            <span>Through measurement traceability, quality and expertise.</span>
          </div>
        </aside>
      </section>

      <section class="section core-services">
        <div class="section-heading">
          <p class="section-kicker">Our Core Services</p>
          <h2>Focused support for meteorological measurement quality</h2>
        </div>
        <div class="service-grid">
          <article v-for="service in services" :key="service.title" class="service-card">
            <span class="icon-tile">
              <component :is="service.icon" />
            </span>
            <div>
              <h3>{{ service.title }}</h3>
              <p>{{ service.description }}</p>
            </div>
            <ArrowRightIcon class="card-arrow" />
          </article>
        </div>
      </section>

      <section class="section capabilities-section">
        <div class="section-bar">
          <div>
            <p class="section-kicker">Calibration Capabilities</p>
            <h2>Key measurement areas</h2>
          </div>
          <a href="#" class="text-link">View all capabilities <ArrowRightIcon /></a>
        </div>

        <div class="capability-grid">
          <article v-for="capability in capabilities" :key="capability.title" class="capability-card">
            <div class="capability-image">
              <img :src="capability.image" :alt="capability.alt" />
              <span class="image-badge">
                <component :is="capability.icon" />
              </span>
            </div>
            <div class="capability-body">
              <h3>{{ capability.title }}</h3>
              <p>{{ capability.range }}</p>
            </div>
          </article>
        </div>
      </section>

      <section class="section news-section">
        <div class="section-bar">
          <div>
            <p class="section-kicker">News & Events</p>
            <h2>Latest activities and service updates</h2>
          </div>
          <a href="#" class="text-link">View all news & events <ArrowRightIcon /></a>
        </div>

        <div class="news-grid">
          <article v-for="item in news" :key="item.title" class="news-card">
            <img :src="item.image" :alt="item.alt" />
            <div class="news-body">
              <time>{{ item.date }}</time>
              <h3>{{ item.title }}</h3>
              <p>{{ item.summary }}</p>
            </div>
          </article>
        </div>
      </section>

      <section class="section quality-section">
        <div>
          <p class="section-kicker">Quality You Can Rely On</p>
          <h2>Built around traceability, standards and WMO recognition</h2>
        </div>
        <div class="quality-grid">
          <article v-for="item in quality" :key="item.title" class="quality-item">
            <component :is="item.icon" />
            <h3>{{ item.title }}</h3>
            <p>{{ item.description }}</p>
          </article>
        </div>
      </section>

      <section class="contact-cta">
        <div>
          <p class="section-kicker">About & Contact</p>
          <h2>Ready to work with RIC Beijing?</h2>
          <p>
            Contact us for calibration requests, technical consultation,
            comparison activities and workshop coordination.
          </p>
        </div>
        <a class="button button-light" href="#">
          Contact Us
          <ArrowRightIcon />
        </a>
      </section>
    </main>

    <footer class="site-footer">
      <span>© 2026 RIC Beijing Regional Instrument Center of RA II.</span>
      <nav aria-label="Footer navigation">
        <a href="#">Privacy Policy</a>
        <a href="#">Terms of Use</a>
        <a href="#">Sitemap</a>
      </nav>
    </footer>
  </div>
</template>

<script setup>
import { h, ref } from 'vue'
import capHumidity from './assets/cap-humidity.png'
import capPrecipitation from './assets/cap-precipitation.png'
import capPressure from './assets/cap-pressure.png'
import capRadiation from './assets/cap-radiation.png'
import capTemperature from './assets/cap-temperature.png'
import capWind from './assets/cap-wind.png'
import newsPyranometer from './assets/news-pyranometer.png'
import newsReport from './assets/news-report.png'
import newsWorkshop from './assets/news-workshop.png'

const MenuIcon = icon('M4 7h16M4 12h16M4 17h16')
const ChevronDownIcon = icon('m7 10 5 5 5-5')
const CalendarIcon = icon('M7 3v4M17 3v4M4 9h16M5 5h14v15H5zM8 13h3v3H8z')
const ChartIcon = icon('M5 19V5M5 19h15M9 16v-5M13 16V8M17 16v-8')
const TargetIcon = icon('M12 4v3M12 17v3M4 12h3M17 12h3M7.8 7.8l2.1 2.1M14.1 14.1l2.1 2.1M16.2 7.8l-2.1 2.1M9.9 14.1l-2.1 2.1M12 9a3 3 0 1 1 0 6 3 3 0 0 1 0-6Z')
const ArrowRightIcon = icon('M5 12h14M13 6l6 6-6 6')
const FlaskIcon = icon('M9 3h6M10 3v6l-5 9a2 2 0 0 0 1.7 3h10.6a2 2 0 0 0 1.7-3l-5-9V3M8 15h8')
const CompareIcon = icon('M7 7h12M15 3l4 4-4 4M17 17H5M9 13l-4 4 4 4')
const HeadsetIcon = icon('M4 13a8 8 0 0 1 16 0v4a3 3 0 0 1-3 3h-2v-7h5M4 13h5v7H7a3 3 0 0 1-3-3v-4')
const ThermometerIcon = icon('M14 14.8V5a2 2 0 1 0-4 0v9.8a4 4 0 1 0 4 0ZM12 6v9')
const DropletIcon = icon('M12 3s6 6.4 6 11a6 6 0 0 1-12 0c0-4.6 6-11 6-11Z')
const GaugeIcon = icon('M4 14a8 8 0 1 1 16 0M12 14l4-4M8 18h8')
const WindIcon = icon('M4 8h11a3 3 0 1 0-3-3M4 12h15M4 16h8a3 3 0 1 1-3 3')
const CloudRainIcon = icon('M7 16a4 4 0 0 1 .7-7.9A5.5 5.5 0 0 1 18 10a3 3 0 0 1-1 6H7ZM8 19v2M12 18v2M16 19v2')
const SunIcon = icon('M12 8a4 4 0 1 1 0 8 4 4 0 0 1 0-8ZM12 2v3M12 19v3M2 12h3M19 12h3M4.9 4.9 7 7M17 17l2.1 2.1M19.1 4.9 17 7M7 17l-2.1 2.1')
const AwardIcon = icon('M12 15a6 6 0 1 0 0-12 6 6 0 0 0 0 12ZM9 14l-1 7 4-2 4 2-1-7')
const ShieldIcon = icon('M12 3 5 6v6c0 4 3 7 7 9 4-2 7-5 7-9V6l-7-3ZM9 12l2 2 4-5')
const DocumentIcon = icon('M7 3h7l5 5v13H7zM14 3v6h5M10 13h6M10 17h6')
const GlobeIcon = icon('M12 21a9 9 0 1 0 0-18 9 9 0 0 0 0 18ZM3 12h18M12 3c3 3.5 3 14.5 0 18M12 3c-3 3.5-3 14.5 0 18')

function icon(path) {
  return () =>
    h(
      'svg',
      {
        viewBox: '0 0 24 24',
        'aria-hidden': 'true',
        fill: 'none',
        stroke: 'currentColor',
        'stroke-width': '1.9',
        'stroke-linecap': 'round',
        'stroke-linejoin': 'round'
      },
      [h('path', { d: path })]
    )
}

const isMenuOpen = ref(false)

const navItems = [
  'Home',
  'About & Contact',
  'Services',
  'Capabilities',
  'Quality',
  'Resources',
  'News & Events'
]

const services = [
  {
    title: 'Calibration Services',
    description: 'Traceable calibration of meteorological instruments and reference standards.',
    icon: FlaskIcon
  },
  {
    title: 'Intercomparison',
    description: 'Support for laboratory and instrument comparison activities.',
    icon: CompareIcon
  },
  {
    title: 'Technical Support',
    description: 'Expert guidance on instrument operation, maintenance and quality assurance.',
    icon: HeadsetIcon
  }
]

const capabilities = [
  {
    title: 'Temperature',
    range: '-90 °C to 60 °C',
    image: capTemperature,
    alt: 'Temperature calibration chamber in a laboratory',
    icon: ThermometerIcon
  },
  {
    title: 'Relative Humidity',
    range: '10 %RH to 98 %RH',
    image: capHumidity,
    alt: 'Clean environmental calibration laboratory',
    icon: DropletIcon
  },
  {
    title: 'Atmospheric Pressure',
    range: '500 hPa to 1100 hPa',
    image: capPressure,
    alt: 'Precision laboratory instruments for pressure measurement',
    icon: GaugeIcon
  },
  {
    title: 'Wind',
    range: '0.2 m/s to 80 m/s',
    image: capWind,
    alt: 'Wind measurement instrument and testing facility',
    icon: WindIcon
  },
  {
    title: 'Precipitation',
    range: '0.1 mm to 300 mm/h',
    image: capPrecipitation,
    alt: 'Outdoor meteorological precipitation equipment',
    icon: CloudRainIcon
  },
  {
    title: 'Radiation / Other',
    range: 'Including solar, UV, evaporation, visibility',
    image: capRadiation,
    alt: 'Solar radiation measurement equipment outdoors',
    icon: SunIcon
  }
]

const news = [
  {
    date: '23-27 Jun 2026',
    title: 'Region II Instrument Calibration Workshop',
    summary: 'A focused training event for calibration methods, uncertainty and laboratory practice.',
    image: newsWorkshop,
    alt: 'Workshop participants discussing technical material'
  },
  {
    date: '28 Apr 2026',
    title: 'New pyranometer calibration service available',
    summary: 'Expanded support for radiation measurement traceability and instrument quality.',
    image: newsPyranometer,
    alt: 'Solar measurement and energy equipment'
  },
  {
    date: '10 Apr 2026',
    title: 'RIC Beijing annual report 2025 published',
    summary: 'Annual activities, capability updates and service statistics are now available.',
    image: newsReport,
    alt: 'Technical report document on a desk'
  }
]

const quality = [
  {
    title: 'ISO/IEC 17025',
    description: 'Accredited quality management system.',
    icon: AwardIcon
  },
  {
    title: 'Traceability',
    description: 'Traceable to SI units through national standards.',
    icon: GlobeIcon
  },
  {
    title: 'WMO Recognition',
    description: 'Designated by the World Meteorological Organization.',
    icon: ShieldIcon
  },
  {
    title: 'Annual Reporting',
    description: 'Regular reporting on activities and capabilities to WMO.',
    icon: DocumentIcon
  }
]

</script>
