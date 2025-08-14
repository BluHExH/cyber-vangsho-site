 cyber-vangsho-site

<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg"
     width="1600" height="400" viewBox="0 0 1600 400" preserveAspectRatio="xMidYMid meet">
  <defs>
    <!-- Neon gradient -->
    <linearGradient id="g1" x1="0" x2="1" y1="0" y2="0">
      <stop offset="0%" stop-color="#39FF14"/>
      <stop offset="35%" stop-color="#00C2FF"/>
      <stop offset="65%" stop-color="#FF39C7"/>
      <stop offset="100%" stop-color="#9D39FF"/>
    </linearGradient>

    <!-- Noise for subtle texture -->
    <filter id="grain">
      <feTurbulence type="fractalNoise" baseFrequency="0.8" numOctaves="1" stitchTiles="stitch" result="n"/>
      <feColorMatrix type="saturate" values="0"/>
      <feBlend in="SourceGraphic" in2="n" mode="overlay"/>
    </filter>

    <!-- Glow -->
    <filter id="glow" x="-50%" y="-50%" width="200%" height="200%">
      <feGaussianBlur stdDeviation="8" result="blur"/>
      <feMerge>
        <feMergeNode in="blur"/>
        <feMergeNode in="blur"/>
        <feMergeNode in="SourceGraphic"/>
      </feMerge>
    </filter>

    <!-- Clip for glitch slices -->
    <clipPath id="slice1">
      <rect x="0" y="0" width="1600" height="120"/>
    </clipPath>
    <clipPath id="slice2">
      <rect x="0" y="140" width="1600" height="60"/>
    </clipPath>
    <clipPath id="slice3">
      <rect x="0" y="220" width="1600" height="90"/>
    </clipPath>

    <!-- Text style as symbol -->
    <symbol id="hexText" viewBox="0 0 1600 400" preserveAspectRatio="xMidYMid meet">
      <text x="50%" y="55%" text-anchor="middle" dominant-baseline="middle"
            font-family="Orbitron, Audiowide, 'Fira Code', sans-serif"
            font-weight="800" font-size="220" letter-spacing="12">
        HEX
      </text>
    </symbol>
  </defs>

  <!-- Background -->
  <rect width="100%" height="100%" fill="#04040a"/>

  <!-- Subtle vignette -->
  <radialGradient id="v" cx="50%" cy="40%">
    <stop offset="0%" stop-color="#00000000"/>
    <stop offset="100%" stop-color="#000000aa"/>
  </radialGradient>
  <rect width="100%" height="100%" fill="url(#v)"/>

  <!-- Base glowing colored text -->
  <g transform="translate(0,0)" filter="url(#glow)">
    <use href="#hexText" fill="url(#g1)" opacity="0.95"/>
  </g>

  <!-- RGB split layers with animation (glitch effect) -->
  <!-- Red-ish layer (shifted) -->
  <g clip-path="url(#slice1)">
    <use href="#hexText" fill="#FF39C7" opacity="0.85">
      <animateTransform attributeName="transform" type="translate"
                        values="0 0; -8 0; 6 0; 0 0" dur="0.9s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.2;0.9;0.4;0.2" dur="1.2s" repeatCount="indefinite"/>
    </use>
  </g>

  <!-- Blue-ish layer -->
  <g clip-path="url(#slice2)">
    <use href="#hexText" fill="#00C2FF" opacity="0.82">
      <animateTransform attributeName="transform" type="translate"
                        values="0 0; 12 0; -6 0; 0 0" dur="1.1s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.3;0.95;0.4;0.3" dur="1.4s" repeatCount="indefinite"/>
    </use>
  </g>

  <!-- Green-ish layer -->
  <g clip-path="url(#slice3)">
    <use href="#hexText" fill="#39FF14" opacity="0.8">
      <animateTransform attributeName="transform" type="translate"
                        values="0 0; -14 0; 10 0; 0 0" dur="0.85s" repeatCount="indefinite"/>
      <animate attributeName="opacity" values="0.25;0.9;0.45;0.25" dur="1.05s" repeatCount="indefinite"/>
    </use>
  </g>

  <!-- White bright flash overlay for occasional flicker -->
  <use href="#hexText" x="0" y="0" fill="#ffffff" opacity="0.0">
    <animate attributeName="opacity" values="0;0;0.6;0;0" keyTimes="0;0.6;0.62;0.8;1" dur="4s" repeatCount="indefinite"/>
  </use>

  <!-- Subtle noise overlay -->
  <rect width="100%" height="100%" filter="url(#grain)" opacity="0.02"/>

  <!-- Static 1-second intro: achieved by delaying heavy animation cycles -->
  <!-- (Many animations loop indefinitely; when converting to GIF set first-frame longer delay) -->

  <!-- Footer small tagline -->
  <text x="50%" y="88%" text-anchor="middle" fill="#c6c6c6" font-family="Inter, Roboto, sans-serif"
        font-size="20" opacity="0.9">BluHExH — Full Stack · Cybersecurity · Open Source</text>
</svg>
