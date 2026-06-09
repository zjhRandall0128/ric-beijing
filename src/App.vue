<template>
  <div class="site-shell">
    <header class="site-header">
      <a class="brand" href="#" aria-label="RIC Beijing home" @click.prevent="navigate('Home')">
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
        <a
          v-for="item in navItems"
          :key="item"
          href="#"
          :class="{ 'is-active': activePage === item }"
          @click.prevent="navigate(item)"
        >
          {{ item }}
        </a>
        <button class="language" type="button">
          <GlobeIcon />
          EN
          <ChevronDownIcon />
        </button>
      </nav>
    </header>

    <main v-if="activePage === 'Home'">
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
            <a class="button button-secondary" href="#" @click.prevent="navigate('Capabilities')">
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
          <a href="#" class="text-link" @click.prevent="navigate('Capabilities')">View all capabilities <ArrowRightIcon /></a>
        </div>

        <div class="capability-grid">
          <article v-for="capability in capabilities" :key="capability.title" class="capability-card">
            <div class="capability-image">
              <span class="capability-photo">
                <img :src="capability.image" :alt="capability.alt" />
              </span>
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

    <main v-else-if="activePage === 'About & Contact'" class="subpage">
      <section class="subpage-hero about-hero">
        <div>
          <p class="eyebrow">About & Contact</p>
          <h1>National metrological support for meteorological observation</h1>
          <p class="hero-copy">
            RIC Beijing is responsible for calibration, verification, testing,
            technical guidance and regional support for meteorological
            observation instruments.
          </p>
        </div>
        <aside class="hero-note capability-note">
          <TargetIcon />
          <div>
            <strong>Contact person: Xi CHEN</strong>
            <span>Calibration requests, technical consultation and RIC coordination.</span>
          </div>
        </aside>
      </section>

      <section class="section about-contact-section">
        <div class="section-bar">
          <div>
            <p class="section-kicker">Contact Us</p>
            <h2>Service contact information</h2>
          </div>
          <a href="mailto:cic121211@163.com" class="text-link">Email RIC Beijing <ArrowRightIcon /></a>
        </div>

        <div class="contact-info-layout">
          <article class="contact-primary-card">
            <p class="section-kicker">Meteorological Observation Centre</p>
            <h3>China Meteorological Administration</h3>
            <p>
              No. 46, Zhongguancun Nandajie (Street), 100081 Beijing, China
            </p>
            <div class="contact-badges">
              <span>Temperature</span>
              <span>Relative Humidity</span>
              <span>Atmospheric Pressure</span>
              <span>Wind</span>
              <span>Precipitation</span>
              <span>Solar Radiation</span>
            </div>
          </article>

          <div class="contact-detail-grid">
            <article v-for="item in contactDetails" :key="item.label" class="contact-detail-card">
              <component :is="item.icon" />
              <span>{{ item.label }}</span>
              <strong>{{ item.value }}</strong>
            </article>
          </div>
        </div>
      </section>

      <section class="section about-us-section">
        <div class="section-bar">
          <div>
            <p class="section-kicker">About Us</p>
            <h2>Role, standards and laboratory capability</h2>
          </div>
        </div>

        <div class="about-narrative-grid">
          <article class="about-story-card">
            <h3>National legal metrological verification institution</h3>
            <p>
              The National Meteorological Station establishes and maintains the
              highest metrological standards in the meteorological industry. It
              carries out meteorological verification, calibration and testing of
              observation instruments, conducts research on observation
              instrument metrological methods, and prepares or revises relevant
              technical specifications and standards.
            </p>
            <p>
              It regularly assesses the quality of national meteorological
              metrology services, submits assessment reports, and undertakes
              provincial meteorological metrology verification business guidance
              and technical training.
            </p>
          </article>

          <div class="about-highlight-list">
            <article v-for="item in aboutHighlights" :key="item.title" class="about-highlight-card">
              <component :is="item.icon" />
              <strong>{{ item.title }}</strong>
              <span>{{ item.description }}</span>
            </article>
          </div>
        </div>

        <div class="standards-panel">
          <div>
            <p class="section-kicker">Laboratory & Accreditation</p>
            <h3>Measurement standards and quality system</h3>
            <p>
              The National Meteorological Measuring Station establishes and
              maintains six highest measurement standards for the meteorological
              industry, covering temperature, air humidity, atmospheric pressure,
              wind speed and direction, precipitation, and solar-earth radiation.
              It has set up 14 measurement laboratories covering temperature,
              humidity, pressure, wind, rain, radiation, sunshine, atmospheric
              electric field, precipitation phenomena, visibility, soil moisture
              and other observation elements.
            </p>
          </div>
          <div class="standards-stat-grid">
            <article>
              <strong>31</strong>
              <span>Authorized verification items</span>
            </article>
            <article>
              <strong>37</strong>
              <span>Calibration items</span>
            </article>
            <article>
              <strong>38</strong>
              <span>Testing items</span>
            </article>
            <article>
              <strong>47</strong>
              <span>CNAS accredited projects</span>
            </article>
          </div>
        </div>
      </section>

      <section class="contact-cta">
        <div>
          <p class="section-kicker">RIC Beijing</p>
          <h2>Need calibration or technical guidance?</h2>
          <p>
            Contact us for capability confirmation, service requests and
            regional meteorological instrument support.
          </p>
        </div>
        <a class="button button-light" href="mailto:cic121211@163.com">
          Contact Us
          <ArrowRightIcon />
        </a>
      </section>
    </main>

    <main v-else-if="activePage === 'Capabilities'" class="subpage">
      <section class="subpage-hero capabilities-hero">
        <div>
          <p class="eyebrow">Calibration Capabilities</p>
          <h1>CNAS-recognized calibration and measurement capability scope</h1>
          <p class="hero-copy">
            Measurement capability ranges for RIC Beijing laboratories, including
            radiation, pressure, temperature, humidity and wind speed instruments.
          </p>
        </div>
        <aside class="hero-note capability-note">
          <GaugeIcon />
          <div>
            <strong>Laboratory capability scope</strong>
            <span>Recognized specifications, ranges and expanded uncertainty, k = 2.</span>
          </div>
        </aside>
      </section>

      <section class="section capability-detail-section">
        <div class="section-bar">
          <div>
            <p class="section-kicker">Measurement Scope</p>
            <h2>Key calibration capabilities</h2>
          </div>
          <a href="#" class="text-link">Download scope document <ArrowRightIcon /></a>
        </div>

        <div class="capability-summary-grid">
          <article v-for="group in capabilityGroups" :key="group.title" class="capability-summary-card">
            <component :is="group.icon" />
            <strong>{{ group.title }}</strong>
            <span>{{ group.description }}</span>
          </article>
        </div>

        <div class="capability-table-card">
          <div class="table-heading">
            <div>
              <p class="section-kicker">CNAS Recognized Scope</p>
              <h3>Laboratory calibration and measurement capability range</h3>
            </div>
            <span>Expanded uncertainty, k = 2</span>
          </div>
          <div class="capability-table-wrap">
            <table class="capability-table">
              <thead>
                <tr>
                  <th>Instrument</th>
                  <th>Measurand</th>
                  <th>Calibration Specification</th>
                  <th>Measurement Range</th>
                  <th>Expanded Uncertainty (k=2)</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in capabilityScope" :key="item.instrument">
                  <td>{{ item.instrument }}</td>
                  <td>{{ item.measurand }}</td>
                  <td>{{ item.specification }}</td>
                  <td v-html="item.range"></td>
                  <td v-html="item.uncertainty"></td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </section>

      <section class="contact-cta">
        <div>
          <p class="section-kicker">Service Request</p>
          <h2>Need a detailed calibration scope?</h2>
          <p>
            Contact RIC Beijing for instrument-specific capability confirmation,
            calibration requirements and technical consultation.
          </p>
        </div>
        <a class="button button-light" href="#">
          Contact Us
          <ArrowRightIcon />
        </a>
      </section>
    </main>

    <main v-else class="subpage">
      <section class="subpage-hero">
        <div>
          <p class="eyebrow">{{ activePage }}</p>
          <h1>{{ activePage }}</h1>
          <p class="hero-copy">
            This section will follow the same RIC Beijing visual system and will
            be developed after the page content is confirmed.
          </p>
        </div>
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
const LocationIcon = icon('M12 21s7-5.4 7-11a7 7 0 1 0-14 0c0 5.6 7 11 7 11ZM12 10.5a2 2 0 1 0 0-4 2 2 0 0 0 0 4Z')
const PersonIcon = icon('M20 21a8 8 0 0 0-16 0M12 13a5 5 0 1 0 0-10 5 5 0 0 0 0 10Z')
const MailIcon = icon('M4 6h16v12H4zM4 7l8 6 8-6')
const PhoneIcon = icon('M7 4h4l2 5-3 2a12 12 0 0 0 5 5l2-3 5 2v4a2 2 0 0 1-2 2A17 17 0 0 1 5 6a2 2 0 0 1 2-2Z')
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
const activePage = ref('Home')

function navigate(page) {
  activePage.value = page
  isMenuOpen.value = false
  window.scrollTo({ top: 0, behavior: 'smooth' })
}

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

const contactDetails = [
  {
    label: 'Contact person',
    value: 'Xi CHEN',
    icon: PersonIcon
  },
  {
    label: 'Email',
    value: 'cic121211@163.com',
    icon: MailIcon
  },
  {
    label: 'Tel',
    value: '010-68400493',
    icon: PhoneIcon
  },
  {
    label: 'Fax',
    value: '010-68409767',
    icon: DocumentIcon
  }
]

const aboutHighlights = [
  {
    title: 'WMO RIC-Beijing',
    description: 'Responsible for the work of RIC-Beijing, the Asian Regional Instrument Center of WMO.',
    icon: GlobeIcon
  },
  {
    title: 'Technical specifications',
    description: 'Prepares and revises meteorological technical specifications and standards.',
    icon: DocumentIcon
  },
  {
    title: 'Quality assessment',
    description: 'Regularly assesses metrology service quality and submits assessment reports.',
    icon: AwardIcon
  },
  {
    title: 'Training guidance',
    description: 'Undertakes provincial verification business guidance and technical training.',
    icon: TargetIcon
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

const capabilityGroups = [
  {
    title: 'Radiation',
    description: 'Total and direct radiation sensitivity calibration.',
    icon: SunIcon
  },
  {
    title: 'Pressure',
    description: 'Digital barometer pressure calibration from 100 hPa to 1200 hPa.',
    icon: GaugeIcon
  },
  {
    title: 'Temperature & Humidity',
    description: 'Standard thermometer and humidity sensor calibration.',
    icon: ThermometerIcon
  },
  {
    title: 'Wind Speed',
    description: 'Cup anemometers, AWS sensors and wind-field instruments.',
    icon: WindIcon
  }
]

const capabilityScope = [
  {
    instrument: 'Total radiometer',
    measurand: 'Sensitivity',
    specification: 'JJG458 Verification Regulation of Total Radiometers',
    range: '(5~25) &micro;V/(W/m&sup2;)',
    uncertainty: 'Urel = 1.6 %'
  },
  {
    instrument: 'Direct radiometer',
    measurand: 'Sensitivity',
    specification: 'JJG456 Verification Regulation of Direct Radiometers',
    range: '(5~15) &micro;V/(W/m&sup2;)',
    uncertainty: 'Urel = 0.6 %'
  },
  {
    instrument: 'Digital barometer',
    measurand: 'Pressure',
    specification: 'JJG1084 Verification Regulation of Digital Barometers',
    range: '(100~1200) hPa',
    uncertainty: 'U = (1~4) Pa'
  },
  {
    instrument: 'Standard mercury thermometer',
    measurand: 'Temperature',
    specification: 'JJG161 Verification Regulation of Standard Mercury Thermometers',
    range: '(-60~80) °C',
    uncertainty: 'U = 0.05 °C'
  },
  {
    instrument: 'Humidity sensor',
    measurand: 'Humidity',
    specification: 'JJF1076 Calibration Specification for Humidity Sensors',
    range: '(5~98) %RH',
    uncertainty: 'U = (0.4~1.5) %RH'
  },
  {
    instrument: 'Portable three-cup wind speed and direction anemometer',
    measurand: 'Wind speed',
    specification: 'JJG431 Verification Regulation of Portable Three-cup Wind Speed and Direction Anemometers',
    range: '(2~30) m/s',
    uncertainty: 'U = 0.07 m/s'
  },
  {
    instrument: 'AWS wind direction and speed sensor',
    measurand: 'Wind speed',
    specification: 'JJG (Meteorology) 004 Verification Regulation of AWS Wind Direction and Speed Sensors',
    range: '(2~40) m/s<br>(40~60) m/s',
    uncertainty: 'U = 0.08 m/s<br>U = (0.08~0.18) m/s'
  },
  {
    instrument: 'Wind-farm electric wind speed sensor',
    measurand: 'Wind speed',
    specification: 'JJF1431 Calibration Specification for Wind-farm Electric Wind Speed Sensors',
    range: '(0.5~2) m/s',
    uncertainty: 'U = (0.25~0.07) m/s'
  },
  {
    instrument: 'Hot-ball anemometer',
    measurand: 'Wind speed',
    specification: 'JJG (Construction) 0001 Verification Regulation of Hot-ball Anemometers',
    range: '(2~30) m/s',
    uncertainty: 'U = 0.07 m/s'
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

