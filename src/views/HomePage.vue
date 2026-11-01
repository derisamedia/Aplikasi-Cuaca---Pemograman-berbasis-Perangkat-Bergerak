<template>
  <ion-page>
    <!-- Konten Utama (Otomatis White saat Siang & Black saat Malam) -->
    <ion-content
      :fullscreen="true"
      :class="['md3-content', 'ion-padding', isMalam ? 'theme-night' : 'theme-day']"
    >
      <!-- Latar Belakang Siluet Perkotaan Halaman -->
      <div class="page-city-bg" aria-hidden="true">
        <svg
          class="page-city-svg"
          viewBox="0 0 1440 360"
          preserveAspectRatio="none"
          fill="none"
        >
          <!-- Lapisan Gedung Jauh -->
          <path
            class="city-layer-far"
            d="M0 360V210H55V165H115V225H160V140H230V200H280V120H350V190H400V150H470V215H520V110H595V185H645V135H710V195H760V95H835V175H890V140H960V205H1015V125H1090V185H1145V150H1220V210H1275V130H1355V195H1440V360H0Z"
          />
          <!-- Lapisan Gedung Menengah -->
          <path
            class="city-layer-mid"
            d="M0 360V245H70V195H135V250H195V175H265V235H325V160H395V225H455V185H530V245H585V150H665V220H720V170H795V235H855V145H930V215H990V175H1065V240H1125V165H1200V225H1265V185H1340V240H1440V360H0Z"
          />
          <!-- Lapisan Gedung Depan -->
          <path
            class="city-layer-near"
            d="M0 360V280H90V230H165V275H240V210H310V265H385V220H465V285H540V195H620V260H690V225H770V280H840V205H920V265H995V230H1075V285H1155V215H1235V270H1315V235H1390V275H1440V360H0Z"
          />
        </svg>
      </div>

      <div class="container">
        <!-- Header Hero Cuaca dengan Background Perkotaan Jakarta -->
        <ion-card class="md3-card hero-weather-card anim-enter">
          <!-- Ilustrasi Siluet Perkotaan & Gedung Pencakar Langit -->
          <div class="hero-cityscape" aria-hidden="true">
            <svg
              class="cityscape-svg"
              viewBox="0 0 800 280"
              preserveAspectRatio="xMidYMax slice"
              fill="none"
            >
              <!-- Elemen Langit Siang (Matahari & Awan Cerah) -->
              <g v-if="!isMalam">
                <circle cx="670" cy="54" r="34" fill="rgba(251, 191, 36, 0.25)" />
                <circle cx="670" cy="54" r="20" fill="rgba(245, 158, 11, 0.45)" />
                <circle cx="150" cy="65" r="65" fill="rgba(255, 255, 255, 0.55)" />
                <circle cx="210" cy="72" r="50" fill="rgba(255, 255, 255, 0.45)" />
              </g>

              <!-- Elemen Langit Malam (Bintang & Bulan Sabit) -->
              <g v-else>
                <circle cx="665" cy="52" r="18" fill="rgba(254, 240, 138, 0.85)" />
                <circle cx="673" cy="47" r="16" fill="#0d1322" />
                <circle cx="110" cy="42" r="1.8" fill="rgba(255, 255, 255, 0.8)" />
                <circle cx="185" cy="28" r="1.4" fill="rgba(255, 255, 255, 0.6)" />
                <circle cx="275" cy="48" r="2" fill="rgba(255, 255, 255, 0.75)" />
                <circle cx="440" cy="30" r="1.5" fill="rgba(255, 255, 255, 0.7)" />
                <circle cx="545" cy="44" r="1.8" fill="rgba(255, 255, 255, 0.65)" />
                <circle cx="595" cy="25" r="1.3" fill="rgba(255, 255, 255, 0.75)" />
              </g>

              <!-- Lapisan Gedung Belakang (Siluet Jauh) -->
              <path
                class="hero-bldg-far"
                d="M0 280V145H42V110H88V155H118V92H172V148H205V78H258V140H295V105H345V155H385V85H435V138H478V68H532V135H572V98H625V148H662V82H718V142H758V108H800V280H0Z"
              />

              <!-- Siluet Monas & Gedung Tengah -->
              <path
                class="hero-monas-body"
                d="M358 150L364 78H372L378 150H358Z"
              />
              <rect
                class="hero-monas-cup"
                x="352"
                y="72"
                width="32"
                height="7"
                rx="3"
              />
              <line
                x1="368"
                y1="54"
                x2="368"
                y2="72"
                stroke="rgba(245, 158, 11, 0.75)"
                stroke-width="2.5"
              />
              <circle cx="368" cy="51" r="4.5" fill="#fbbf24" />

              <!-- Lapisan Gedung Utama Perkotaan -->
              <path
                class="hero-bldg-mid"
                d="M0 280V178H35V132H82V182H108V118H156V174H188V102H242V168H274V136H322V184H412V114H466V176H498V94H554V166H592V126H646V180H682V106H738V170H772V138H800V280H0Z"
              />

              <!-- Lapisan Gedung Depan -->
              <path
                class="hero-bldg-near"
                d="M0 280V205H50V168H98V212H142V152H195V204H238V172H292V216H342V162H398V208H448V148H505V206H552V166H608V214H654V156H710V206H756V176H800V280H0Z"
              />

              <!-- Detail Jendela Gedung (Kaca Siang / Lampu Menyala Malam) -->
              <g class="hero-windows">
                <rect x="120" y="130" width="6" height="6" rx="1" />
                <rect x="132" y="130" width="6" height="6" rx="1" />
                <rect x="120" y="142" width="6" height="6" rx="1" />
                <rect x="198" y="114" width="6" height="6" rx="1" />
                <rect x="210" y="114" width="6" height="6" rx="1" />
                <rect x="222" y="114" width="6" height="6" rx="1" />
                <rect x="198" y="126" width="6" height="6" rx="1" />
                <rect x="222" y="126" width="6" height="6" rx="1" />
                <rect x="198" y="138" width="6" height="6" rx="1" />
                <rect x="210" y="138" width="6" height="6" rx="1" />

                <rect x="424" y="126" width="6" height="6" rx="1" />
                <rect x="436" y="126" width="6" height="6" rx="1" />
                <rect x="448" y="126" width="6" height="6" rx="1" />
                <rect x="424" y="138" width="6" height="6" rx="1" />
                <rect x="448" y="138" width="6" height="6" rx="1" />

                <rect x="510" y="108" width="6" height="6" rx="1" />
                <rect x="522" y="108" width="6" height="6" rx="1" />
                <rect x="534" y="108" width="6" height="6" rx="1" />
                <rect x="510" y="120" width="6" height="6" rx="1" />
                <rect x="522" y="120" width="6" height="6" rx="1" />
                <rect x="510" y="132" width="6" height="6" rx="1" />
                <rect x="534" y="132" width="6" height="6" rx="1" />

                <rect x="694" y="118" width="6" height="6" rx="1" />
                <rect x="706" y="118" width="6" height="6" rx="1" />
                <rect x="718" y="118" width="6" height="6" rx="1" />
                <rect x="694" y="130" width="6" height="6" rx="1" />
                <rect x="706" y="130" width="6" height="6" rx="1" />
              </g>
            </svg>
          </div>

          <ion-card-content class="hero-weather-body">
            <!-- Bagian Atas Header: Kiri Atas (Jakarta & Kondisi) dan Kanan Atas (Suhu Besar) -->
            <div class="hero-top-bar">
              <div class="hero-left">
                <div class="title-time-row">
                  <h2 class="jakarta-title">Jakarta</h2>
                  <button
                    type="button"
                    class="time-mode-pill"
                    :title="'Klik untuk beralih mode tampilan (Saat ini: ' + labelModeWaktu + ')'"
                    @click="gantiModeWaktu"
                  >
                    <span>{{ isMalam ? '🌙 Malam' : '☀️ Siang' }}</span>
                    <span class="pill-sep">•</span>
                    <span>{{ jamMenitSekarang }} WIB</span>
                  </button>
                </div>
                <div class="condition-row">
                  <svg class="condition-svg" viewBox="0 0 36 36" fill="none">
                    <!-- Matahari saat Siang / Bulan saat Malam -->
                    <circle
                      v-if="!isMalam"
                      cx="16"
                      cy="14"
                      r="7"
                      fill="#FFC107"
                    />
                    <path
                      v-else
                      d="M19.5 8.5C15.9 9.2 13.5 12.6 14.2 16.2C14.9 19.8 18.3 22.2 21.9 21.5C20.2 22.8 17.9 23.3 15.6 22.7C11.6 21.7 9.2 17.6 10.2 13.6C11.1 10.1 14.3 7.8 17.8 8.1C18.4 8.1 19 8.3 19.5 8.5Z"
                      fill="#FDE047"
                    />
                    <path
                      d="M13.5 24.5H24.5C27.26 24.5 29.5 22.26 29.5 19.5C29.5 16.92 27.54 14.8 25.03 14.53C24.22 11.36 21.36 9 17.95 9C13.92 9 10.65 12.27 10.65 16.3C10.65 16.58 10.67 16.85 10.7 17.12C8.88 17.64 7.55 19.31 7.55 21.3C7.55 23.07 8.98 24.5 10.75 24.5H13.5Z"
                      :fill="isMalam ? '#3E4E6C' : '#93C5FD'"
                      :stroke="isMalam ? '#B0BEC5' : '#3B82F6'"
                      stroke-width="1.8"
                      stroke-linejoin="round"
                    />
                  </svg>
                  <span class="condition-text">
                    {{ isMalam ? 'Malam berawan' : 'Cerah berawan' }}
                  </span>
                </div>
              </div>

              <div class="hero-right">
                <div class="main-temp">
                  <span class="temp-digits">{{ suhuUtama }}</span>
                  <span class="temp-degree">°</span>
                </div>
              </div>
            </div>

            <!-- Informasi Lokasi API (Latitude, Longitude, Zona Waktu, Satuan) -->
            <ion-grid class="ion-no-padding meta-grid">
              <ion-row>
                <ion-col size="6" size-sm="3">
                  <div class="meta-box">
                    <span class="meta-label">Latitude</span>
                    <strong class="meta-value">{{ infoLokasi.latitude }}</strong>
                  </div>
                </ion-col>
                <ion-col size="6" size-sm="3">
                  <div class="meta-box">
                    <span class="meta-label">Longitude</span>
                    <strong class="meta-value">{{ infoLokasi.longitude }}</strong>
                  </div>
                </ion-col>
                <ion-col size="6" size-sm="3">
                  <div class="meta-box">
                    <span class="meta-label">Zona Waktu</span>
                    <strong class="meta-value">{{ infoLokasi.timezone }}</strong>
                  </div>
                </ion-col>
                <ion-col size="6" size-sm="3">
                  <div class="meta-box">
                    <span class="meta-label">Satuan Suhu</span>
                    <strong class="meta-value">{{ satuanSuhu }}</strong>
                  </div>
                </ion-col>
              </ion-row>
            </ion-grid>
          </ion-card-content>
        </ion-card>

        <!-- Pilihan Jumlah Data -->
        <ion-card class="md3-card anim-enter anim-delay-1">
          <ion-card-content>
            <div class="control-group">
              <span class="control-title">Jumlah Data Ditampilkan:</span>
              <ion-segment v-model="batasData" mode="ios" class="md3-segment">
                <ion-segment-button value="10">
                  <ion-label>10 Data Pertama</ion-label>
                </ion-segment-button>
                <ion-segment-button value="24">
                  <ion-label>24 Jam Pertama</ion-label>
                </ion-segment-button>
                <ion-segment-button value="semua">
                  <ion-label>Semua ({{ daftarCuaca.length }})</ion-label>
                </ion-segment-button>
              </ion-segment>
            </div>
          </ion-card-content>
        </ion-card>

        <!-- Transisi Animasi Material 3 -->
        <Transition name="md3-fade" mode="out-in">
          <!-- Indikator Loading -->
          <div v-if="loading" key="loading" class="state-box">
            <ion-spinner name="crescent" color="primary"></ion-spinner>
            <p>Sedang mengambil data cuaca dari API Open-Meteo...</p>
          </div>

          <!-- Pesan Error Jika Gagal Fetch -->
          <ion-card v-else-if="pesanError" key="error" class="md3-card" color="danger">
            <ion-card-header>
              <ion-card-title>Gagal Memuat Data</ion-card-title>
            </ion-card-header>
            <ion-card-content>
              <p>{{ pesanError }}</p>
              <ion-button color="light" shape="round" size="small" @click="ambilDataCuaca">
                Coba Lagi
              </ion-button>
            </ion-card-content>
          </ion-card>

          <!-- Tabel Data Cuaca -->
          <ion-card v-else :key="batasData" class="md3-card">
            <ion-card-header>
              <ion-card-title>
                Data Prakiraan Cuaca Per Jam ({{ dataDitampilkan.length }} Data)
              </ion-card-title>
              <ion-card-subtitle>
                Menampilkan atribut <code>time</code> dan <code>temperature_2m</code>
              </ion-card-subtitle>
            </ion-card-header>

            <ion-card-content>
              <div class="table-responsive">
                <table class="weather-table">
                  <thead>
                    <tr>
                      <th class="text-center">No</th>
                      <th>time (Waktu Pengukuran)</th>
                      <th>Waktu</th>
                      <th>temperature_2m (Suhu °C)</th>
                      <th class="text-center">Keterangan</th>
                    </tr>
                  </thead>
                  <tbody>
                    <tr
                      v-for="(item, index) in dataDitampilkan"
                      :key="item.time"
                      class="row-anim"
                      :style="{ '--i': Math.min(index, 15) }"
                    >
                      <td class="text-center">
                        <span class="no-badge">{{ index + 1 }}</span>
                      </td>
                      <td>
                        <code class="time-code">{{ item.time }}</code>
                      </td>
                      <td>{{ formatWaktu(item.time) }}</td>
                      <td class="temp-cell">
                        <strong>{{ item.temperature_2m }} {{ satuanSuhu }}</strong>
                      </td>
                      <td class="text-center">
                        <ion-badge class="status-badge" :color="warnaSuhu(item.temperature_2m)">
                          {{ labelSuhu(item.temperature_2m) }}
                        </ion-badge>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </div>
            </ion-card-content>
          </ion-card>
        </Transition>
      </div>
    </ion-content>
  </ion-page>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'
import {
  IonPage,
  IonButton,
  IonContent,
  IonCard,
  IonCardHeader,
  IonCardTitle,
  IonCardSubtitle,
  IonCardContent,
  IonLabel,
  IonBadge,
  IonSegment,
  IonSegmentButton,
  IonSpinner,
  IonGrid,
  IonRow,
  IonCol,
} from '@ionic/vue'

const API_URL =
  'https://api.open-meteo.com/v1/forecast?latitude=-6.2&longitude=106.8&hourly=temperature_2m'

const daftarCuaca = ref([])
const satuanSuhu = ref('°C')
const infoLokasi = ref({
  latitude: -6.2,
  longitude: 106.8,
  timezone: 'GMT',
})
const loading = ref(true)
const pesanError = ref('')

const batasData = ref('10')

const waktuSekarang = ref(new Date())
const modeWaktu = ref('auto')
let timerJam = null

const jamSekarang = computed(() => waktuSekarang.value.getHours())

const jamMenitSekarang = computed(() => {
  const jam = String(waktuSekarang.value.getHours()).padStart(2, '0')
  const menit = String(waktuSekarang.value.getMinutes()).padStart(2, '0')
  return `${jam}:${menit}`
})

const isMalam = computed(() => {
  if (modeWaktu.value === 'malam') return true
  if (modeWaktu.value === 'siang') return false
  return jamSekarang.value < 6 || jamSekarang.value >= 18
})

const labelModeWaktu = computed(() => {
  if (modeWaktu.value === 'auto') {
    return `Otomatis (${isMalam.value ? 'Malam' : 'Siang'})`
  }
  return modeWaktu.value === 'malam' ? 'Manual Malam' : 'Manual Siang'
})

function gantiModeWaktu() {
  if (modeWaktu.value === 'auto') {
    modeWaktu.value = isMalam.value ? 'siang' : 'malam'
  } else if (modeWaktu.value === 'siang') {
    modeWaktu.value = 'malam'
  } else {
    modeWaktu.value = 'auto'
  }
}

const dataDitampilkan = computed(() => {
  if (batasData.value === '10') {
    return daftarCuaca.value.slice(0, 10)
  }
  if (batasData.value === '24') {
    return daftarCuaca.value.slice(0, 24)
  }
  return daftarCuaca.value
})

const suhuUtama = computed(() => {
  if (!daftarCuaca.value.length) return 28
  const indexJam = Math.min(jamSekarang.value, daftarCuaca.value.length - 1)
  return Math.round(daftarCuaca.value[indexJam].temperature_2m)
})

async function ambilDataCuaca() {
  loading.value = true
  pesanError.value = ''

  try {
    const response = await fetch(API_URL)
    if (!response.ok) {
      throw new Error(`HTTP Error! Status: ${response.status}`)
    }

    const data = await response.json()

    infoLokasi.value = {
      latitude: data.latitude,
      longitude: data.longitude,
      timezone: data.timezone || 'GMT',
    }
    satuanSuhu.value = data.hourly_units?.temperature_2m || '°C'

    const arrayTime = data.hourly?.time || []
    const arrayTemp = data.hourly?.temperature_2m || []

    daftarCuaca.value = arrayTime.map((waktu, index) => ({
      time: waktu,
      temperature_2m: arrayTemp[index],
    }))
  } catch (error) {
    pesanError.value =
      'Gagal mengambil data dari server Open-Meteo: ' + error.message
  } finally {
    loading.value = false
  }
}

function formatWaktu(isoString) {
  if (!isoString) return '-'
  const [tanggal, jam] = isoString.split('T')
  return `${tanggal} Pukul ${jam}`
}

function warnaSuhu(suhu) {
  if (suhu >= 31) return 'danger'
  if (suhu >= 28) return 'warning'
  return 'success'
}

function labelSuhu(suhu) {
  if (suhu >= 31) return 'Panas'
  if (suhu >= 28) return 'Hangat'
  return 'Sejuk'
}

onMounted(() => {
  ambilDataCuaca()
  timerJam = setInterval(() => {
    waktuSekarang.value = new Date()
  }, 30000)
})

onUnmounted(() => {
  if (timerJam) clearInterval(timerJam)
})
</script>

<style scoped>
/* =========================================================
   TEMA DINAMIS SIANG (WHITE) & MALAM (BLACK) + PERKOTAAN
   ========================================================= */
.md3-content {
  font-family: 'Plus Jakarta Sans', system-ui, -apple-system, sans-serif;
  transition: background 350ms ease, color 350ms ease;
}

/* --- TEMA SIANG (WHITE) --- */
.md3-content.theme-day {
  --background: linear-gradient(180deg, #ffffff 0%, #f4f7fc 58%, #e6eef9 100%);
  color: #0f172a;
}

.theme-day .city-layer-far {
  fill: rgba(30, 64, 175, 0.06);
}
.theme-day .city-layer-mid {
  fill: rgba(30, 64, 175, 0.1);
}
.theme-day .city-layer-near {
  fill: rgba(30, 64, 175, 0.14);
}

/* --- TEMA MALAM (BLACK) --- */
.md3-content.theme-night {
  --background: linear-gradient(180deg, #000000 0%, #070b14 55%, #0f172a 100%);
  color: #f8fafc;
}

.theme-night .city-layer-far {
  fill: rgba(148, 163, 184, 0.06);
}
.theme-night .city-layer-mid {
  fill: rgba(148, 163, 184, 0.1);
}
.theme-night .city-layer-near {
  fill: rgba(148, 163, 184, 0.15);
}

.page-city-bg {
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 0;
  display: flex;
  align-items: flex-end;
  overflow: hidden;
}

.page-city-svg {
  width: 100%;
  height: 320px;
  display: block;
}

.container {
  position: relative;
  z-index: 1;
  max-width: 900px;
  margin: 0 auto;
  padding-bottom: 24px;
}

/* Kartu Material 3 (Siang vs Malam) */
.md3-card {
  margin: 0 0 16px;
  border-radius: 28px;
  backdrop-filter: blur(12px);
  transition:
    background-color 300ms ease,
    border-color 300ms ease,
    box-shadow 300ms ease;
}

.theme-day .md3-card {
  background: rgba(255, 255, 255, 0.94);
  box-shadow: 0 4px 20px rgba(15, 23, 42, 0.06);
  border: 1px solid #e2e8f0;
}

.theme-night .md3-card {
  background: rgba(15, 20, 30, 0.92);
  box-shadow: 0 6px 24px rgba(0, 0, 0, 0.55);
  border: 1px solid rgba(255, 255, 255, 0.1);
}

.theme-day .md3-card ion-card-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: #0f172a;
}

.theme-night .md3-card ion-card-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: #f8fafc;
}

.theme-day .md3-card ion-card-subtitle {
  font-size: 0.85rem;
  color: #475569;
  text-transform: none;
}

.theme-night .md3-card ion-card-subtitle {
  font-size: 0.85rem;
  color: #94a3b8;
  text-transform: none;
}

/* =========================================================
   HEADER HERO CUACA DENGAN SILUET PERKOTAAN JAKARTA
   ========================================================= */
.hero-weather-card {
  position: relative;
  overflow: hidden;
}

/* Hero Card Siang (White / Daylight Urban) */
.theme-day .hero-weather-card {
  background: linear-gradient(180deg, #ffffff 0%, #f0f6ff 55%, #dbeafe 100%);
  border: 1px solid #cbd5e1;
  color: #0f172a;
  box-shadow: 0 10px 28px rgba(37, 99, 235, 0.12);
}

/* Hero Card Malam (Black / Night Urban) */
.theme-night .hero-weather-card {
  background: linear-gradient(180deg, #050811 0%, #0f172a 55%, #1e293b 100%);
  border: 1px solid rgba(255, 255, 255, 0.12);
  color: #ffffff;
  box-shadow: 0 10px 28px rgba(0, 0, 0, 0.65);
}

.hero-cityscape {
  position: absolute;
  inset: 0;
  pointer-events: none;
  z-index: 0;
}

.cityscape-svg {
  width: 100%;
  height: 100%;
  display: block;
}

/* Warna Gedung Hero saat Siang (White Theme) */
.theme-day .hero-bldg-far {
  fill: rgba(59, 130, 246, 0.1);
}
.theme-day .hero-monas-body,
.theme-day .hero-monas-cup {
  fill: rgba(37, 99, 235, 0.22);
}
.theme-day .hero-bldg-mid {
  fill: rgba(37, 99, 235, 0.16);
}
.theme-day .hero-bldg-near {
  fill: rgba(29, 78, 216, 0.24);
}
.theme-day .hero-windows {
  fill: rgba(255, 255, 255, 0.75);
}

/* Warna Gedung Hero saat Malam (Black Theme) */
.theme-night .hero-bldg-far {
  fill: rgba(2, 6, 23, 0.45);
}
.theme-night .hero-monas-body,
.theme-night .hero-monas-cup {
  fill: rgba(2, 6, 23, 0.7);
}
.theme-night .hero-bldg-mid {
  fill: rgba(2, 6, 23, 0.65);
}
.theme-night .hero-bldg-near {
  fill: rgba(0, 0, 0, 0.82);
}
.theme-night .hero-windows {
  fill: rgba(253, 224, 71, 0.55);
}

.hero-weather-body {
  position: relative;
  z-index: 1;
  padding: 24px 22px 20px;
}

.hero-top-bar {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 18px;
}

.hero-left {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 6px;
}

.title-time-row {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 10px;
}

.jakarta-title {
  margin: 0;
  font-size: 2rem;
  font-weight: 700;
  letter-spacing: -0.02em;
  line-height: 1.15;
}

.theme-day .jakarta-title {
  color: #0f172a;
}

.theme-night .jakarta-title {
  color: #ffffff;
}

.time-mode-pill {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 5px 12px;
  border-radius: 999px;
  font-size: 0.78rem;
  font-weight: 600;
  cursor: pointer;
  transition: transform 180ms ease, background-color 200ms ease;
}

.time-mode-pill:active {
  transform: scale(0.95);
}

.theme-day .time-mode-pill {
  background: rgba(15, 23, 42, 0.08);
  border: 1px solid rgba(15, 23, 42, 0.12);
  color: #0f172a;
}

.theme-night .time-mode-pill {
  background: rgba(255, 255, 255, 0.12);
  border: 1px solid rgba(255, 255, 255, 0.2);
  color: #f8fafc;
}

.pill-sep {
  opacity: 0.6;
}

.condition-row {
  display: inline-flex;
  align-items: center;
  gap: 8px;
}

.condition-svg {
  width: 28px;
  height: 28px;
}

.condition-text {
  font-size: 1.05rem;
  font-weight: 500;
}

.theme-day .condition-text {
  color: #334155;
}

.theme-night .condition-text {
  color: #e2e8f0;
}

.hero-right {
  display: flex;
  align-items: flex-start;
}

.main-temp {
  display: inline-flex;
  align-items: flex-start;
  line-height: 1;
  font-family: 'Quicksand', 'Plus Jakarta Sans', sans-serif;
}

.temp-digits {
  font-size: 4.5rem;
  font-weight: 600;
  letter-spacing: -0.04em;
}

.temp-degree {
  font-size: 2.8rem;
  font-weight: 600;
  margin-top: 2px;
  margin-left: 2px;
}

.theme-day .temp-digits,
.theme-day .temp-degree {
  color: #0f172a;
}

.theme-night .temp-digits,
.theme-night .temp-degree {
  color: #ffffff;
}

.meta-grid {
  margin-top: 8px;
}

.meta-box {
  border-radius: 16px;
  padding: 10px 12px;
  margin: 4px;
  display: flex;
  flex-direction: column;
  text-align: center;
  transition:
    transform 250ms cubic-bezier(0.22, 1.25, 0.36, 1),
    background-color 200ms ease;
}

.theme-day .meta-box {
  background: rgba(255, 255, 255, 0.82);
  border: 1px solid rgba(15, 23, 42, 0.1);
}

.theme-day .meta-box:hover {
  transform: translateY(-2px);
  background: rgba(255, 255, 255, 0.96);
}

.theme-night .meta-box {
  background: rgba(0, 0, 0, 0.45);
  border: 1px solid rgba(255, 255, 255, 0.14);
}

.theme-night .meta-box:hover {
  transform: translateY(-2px);
  background: rgba(0, 0, 0, 0.65);
}

.meta-label {
  font-size: 0.75rem;
}

.theme-day .meta-label {
  color: #475569;
}

.theme-night .meta-label {
  color: rgba(255, 255, 255, 0.75);
}

.meta-value {
  font-size: 1rem;
  margin-top: 2px;
}

.theme-day .meta-value {
  color: #0f172a;
}

.theme-night .meta-value {
  color: #ffffff;
}

/* =========================================================
   SEGMENTED CONTROL & TABEL DATA CUACA (SIANG & MALAM)
   ========================================================= */
.control-group {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.control-title {
  font-size: 0.85rem;
  font-weight: 600;
}

.theme-day .control-title {
  color: #334155;
}

.theme-night .control-title {
  color: #cbd5e1;
}

.md3-segment {
  border-radius: 999px;
  padding: 4px;
}

.theme-day .md3-segment {
  --background: #eaeef6;
}

.theme-night .md3-segment {
  --background: #1e293b;
}

.md3-segment ion-segment-button {
  --border-radius: 999px;
  font-weight: 600;
  min-height: 36px;
}

.theme-day .md3-segment ion-segment-button {
  --indicator-color: #d3e3fd;
  --color: #444746;
  --color-checked: #041e49;
}

.theme-night .md3-segment ion-segment-button {
  --indicator-color: #334155;
  --color: #94a3b8;
  --color-checked: #ffffff;
}

.state-box {
  text-align: center;
  padding: 40px 16px;
}

.table-responsive {
  overflow-x: auto;
  border-radius: 16px;
}

.theme-day .table-responsive {
  border: 1px solid #e1e6f0;
}

.theme-night .table-responsive {
  border: 1px solid #1e293b;
}

.weather-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.94rem;
}

.weather-table th,
.weather-table td {
  padding: 12px 14px;
  text-align: left;
  vertical-align: middle;
}

.theme-day .weather-table th,
.theme-day .weather-table td {
  border-bottom: 1px solid #eaeef6;
  color: #1e293b;
}

.theme-night .weather-table th,
.theme-night .weather-table td {
  border-bottom: 1px solid #1e293b;
  color: #e2e8f0;
}

.weather-table th {
  font-weight: 700;
  font-size: 0.84rem;
}

.theme-day .weather-table th {
  background-color: #f0f4f9;
  color: #041e49;
}

.theme-night .weather-table th {
  background-color: #161f30;
  color: #f8fafc;
}

.weather-table tbody tr {
  transition: background-color 180ms cubic-bezier(0.2, 0, 0, 1);
}

.theme-day .weather-table tbody tr:hover {
  background-color: #f4f7fc;
}

.theme-night .weather-table tbody tr:hover {
  background-color: rgba(255, 255, 255, 0.04);
}

.weather-table tbody tr:last-child td {
  border-bottom: none;
}

.text-center {
  text-align: center !important;
}

.no-badge {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 28px;
  height: 28px;
  border-radius: 50%;
  font-size: 0.82rem;
  font-weight: 600;
}

.theme-day .no-badge {
  background-color: #eaeef6;
  color: #041e49;
}

.theme-night .no-badge {
  background-color: #1e293b;
  color: #e2e8f0;
}

.time-code {
  padding: 4px 8px;
  border-radius: 8px;
  font-size: 0.84rem;
}

.theme-day .time-code {
  background-color: #f0f4f9;
  color: #273974;
}

.theme-night .time-code {
  background-color: #1e293b;
  color: #93c5fd;
}

.temp-cell {
  font-size: 1.02rem;
}

.theme-day .temp-cell {
  color: #1d4ed8;
}

.theme-night .temp-cell {
  color: #60a5fa;
}

.status-badge {
  padding: 6px 12px;
  border-radius: 999px;
  font-weight: 600;
  font-size: 0.8rem;
}

/* =========================================================
   ANIMASI MATERIAL DESIGN 3
   ========================================================= */
.anim-enter {
  animation: md3SlideUp 450ms cubic-bezier(0.05, 0.7, 0.1, 1) both;
}

.anim-delay-1 {
  animation-delay: 70ms;
}

.row-anim {
  animation: md3RowFade 350ms cubic-bezier(0.05, 0.7, 0.1, 1) both;
  animation-delay: calc(var(--i, 0) * 25ms);
}

@keyframes md3SlideUp {
  from {
    opacity: 0;
    transform: translateY(16px) scale(0.985);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes md3RowFade {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.md3-fade-enter-active {
  transition:
    opacity 280ms cubic-bezier(0.05, 0.7, 0.1, 1),
    transform 280ms cubic-bezier(0.05, 0.7, 0.1, 1);
}

.md3-fade-leave-active {
  transition:
    opacity 150ms cubic-bezier(0.3, 0, 0.8, 0.15),
    transform 150ms cubic-bezier(0.3, 0, 0.8, 0.15);
}

.md3-fade-enter-from {
  opacity: 0;
  transform: scale(0.98) translateY(8px);
}

.md3-fade-leave-to {
  opacity: 0;
  transform: scale(0.99) translateY(-6px);
}
</style>
