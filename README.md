# Horoscope API - DivineAPI

> The complete **Horoscope API** for developers. Daily, weekly, monthly and yearly zodiac predictions, plus Chinese and numerology horoscope systems. Six REST endpoints covering every horoscope cadence your app will ever need. Plain JSON over HTTPS, 25 languages, no SDK required.

[![Get API Key](https://img.shields.io/badge/Get%20API%20Key-cb22e6?style=for-the-badge&logoColor=white)](https://divineapi.com/register)
[![Live Docs](https://img.shields.io/badge/Live%20Docs-4F46E5?style=for-the-badge&logoColor=white)](https://developers.divineapi.com/horoscope-and-tarot-api)
[![API Status](https://img.shields.io/badge/API%20Status-10b981?style=for-the-badge&logoColor=white)](https://status.divineapi.com)
[![14-Day Free Trial](https://img.shields.io/badge/14--Day%20Free%20Trial-039BE5?style=for-the-badge&logoColor=white)](https://divineapi.com/register)
[![Postman](https://img.shields.io/badge/Run%20in%20Postman-FF6C37?style=for-the-badge&logoColor=white)](https://documenter.getpostman.com/view/26759678/2sBXitCnDX)

<p align="center">
  <img src="https://developers.divineapi.com/public/assets/web/images/divineIcon.svg" alt="DivineAPI, Horoscope API for developers" width="120" />
</p>

---

## What is the Horoscope API?

The **Horoscope API** by DivineAPI is a curated suite of 6 REST endpoints that powers every horoscope feature a modern astrology product needs. Point it at a zodiac sign, get back a well-written prediction broken into six life areas (personal, health, profession, emotions, travel, luck). Each cadence, daily, weekly, monthly, yearly, is its own endpoint, so you can refresh content at exactly the frequency your app needs without wasting calls.

Two extra endpoints extend your horoscope offering beyond Western astrology: a **Chinese Horoscope** (zodiac animal based on birth year) and a **Numerology Horoscope** (guidance derived from numerology numbers). All endpoints return plain JSON over HTTPS, support 25 languages, and work from any stack, no SDK required.

Part of the broader [DivineAPI platform](https://github.com/DivineAPI/astrology-api) (200+ astrology, horoscope, tarot and numerology endpoints).

## Common use cases

| Use case | Endpoint to pick |
|---|---|
| **Daily horoscope widget** on a homepage or blog | Daily Horoscope |
| **Weekly newsletter / email campaign** | Weekly Horoscope |
| **Mobile app push notifications** (once per day) | Daily Horoscope |
| **Monthly dashboard** or themed content page | Monthly Horoscope |
| **"Year ahead" premium content** (paid tier, generated once) | Yearly Horoscope |
| **"What's your Chinese zodiac?" onboarding flow** | Chinese Horoscope |
| **Numerology-led advice app** | Numerology Horoscope |
| **Social / sharing feature** ("your horoscope today") | Daily or Weekly |

## Why choose DivineAPI's Horoscope API?

- **6 horoscope cadences in one API key**: daily, weekly, monthly, yearly, Chinese, numerology
- **Six-section predictions**: personal, health, profession, emotions, travel, luck, each written by professional astrologers
- **All 12 Western zodiac signs** supported (Aries through Pisces)
- **Chinese zodiac animal** auto-derived from birth year
- **Language-aware**: request predictions in 25 languages (English, Hindi, Spanish, French, Arabic, Chinese, and more)
- **Timezone-aware**: correct "today" for any user, anywhere in the world
- **Stable, cacheable** responses for any given (sign, date, tzone, lan) tuple, perfect for CDN or edge caching
- **No SDK lock-in**: plain JSON over HTTPS, works with every language
- **Live status page**: uptime monitored at [status.divineapi.com](https://status.divineapi.com)
- **Postman collection** included: import and run in seconds

## All endpoints in the Horoscope API

### Western Zodiac Horoscopes

| Endpoint | When to use | Docs |
|---|---|---|
| Daily Horoscope Prediction | New content every day; widgets, notifications | [link](https://developers.divineapi.com/horoscope-and-tarot-api/daily-horoscope-prediction) |
| Weekly Horoscope Prediction | Newsletters, weekly email campaigns | [link](https://developers.divineapi.com/horoscope-and-tarot-api/weekly-horoscope-prediction) |
| Monthly Horoscope Prediction | Monthly dashboard pages, magazines | [link](https://developers.divineapi.com/horoscope-and-tarot-api/monthly-horoscope-prediction) |
| Yearly Horoscope Prediction | Premium "year ahead" content, annual reports | [link](https://developers.divineapi.com/horoscope-and-tarot-api/yearly-horoscope-prediction) |

### Alternative Horoscope Systems

| Endpoint | When to use | Docs |
|---|---|---|
| Chinese Horoscope | Chinese zodiac animal readings based on birth year | [link](https://developers.divineapi.com/horoscope-and-tarot-api/chinese-horoscope) |
| Numerology Horoscope | Number-driven daily guidance for numerology apps | [link](https://developers.divineapi.com/horoscope-and-tarot-api/numerology-horoscope) |

Full reference, request/response samples, and live "try-it" console → **[developers.divineapi.com/horoscope-and-tarot-api](https://developers.divineapi.com/horoscope-and-tarot-api)**

---

## Quick start

1. **Get your API key** → [divineapi.com/register](https://divineapi.com/register) (14-day free trial, no credit card)
2. **Make your first call** - see the walkthrough below
3. **Browse all endpoints** → [developers.divineapi.com/horoscope-and-tarot-api](https://developers.divineapi.com/horoscope-and-tarot-api)

---

## Walkthrough: Daily Horoscope Prediction

The flagship endpoint. Pass a zodiac sign and a day (`today`, `tomorrow`, `yesterday`), get back a six-section prediction tailored to that sign for that day.

```http
POST https://astroapi-5.divineapi.com/api/v5/daily-horoscope
```

Authenticate with a Bearer token in the `Authorization` header **and** pass `api_key` in the request body (both required).

### Request body

| Parameter | Type | Required | Description | Example |
|---|---|:---:|---|---|
| `api_key` | string | ✓ | Your DivineAPI key | `YOUR_API_KEY` |
| `sign` | string | ✓ | Zodiac sign (lowercase) | `leo` |
| `h_day` | string | ✓ | One of `today`, `tomorrow`, `yesterday` | `today` |
| `tzone` | float | ✓ | User's timezone offset from UTC | `5.5` |
| `lan` | string | - | Language code (default `en`) | `en` |

**Supported signs:** `aries`, `taurus`, `gemini`, `cancer`, `leo`, `virgo`, `libra`, `scorpio`, `sagittarius`, `capricorn`, `aquarius`, `pisces`.

Full docs → **[developers.divineapi.com/horoscope-and-tarot-api/daily-horoscope-prediction](https://developers.divineapi.com/horoscope-and-tarot-api/daily-horoscope-prediction)**

### Sample response

```json
{
  "success": 1,
  "data": {
    "sign": "Leo",
    "date": "2025-10-07",
    "prediction": {
      "personal":   "Your personal life is full of vibrant energy today, encouraging you to connect with those around you. Spend quality time with family and friends...",
      "health":     "Pay attention to physical wellness today, Leo. A balanced approach to nutrition and hydration will keep you energized. Incorporate moderate exercise...",
      "profession": "Today, you may find yourself inspired at work, Leo. New ideas are likely to flow freely, and you could impress colleagues with your creativity...",
      "emotions":   "Your emotional landscape is rich with inspiration today...",
      "travel":     "A short trip or local outing could bring unexpected joy...",
      "luck": [
        "Colors of the day: Gold, Crimson",
        "Lucky Numbers: 3, 8",
        "Lucky Alphabets: L, S",
        "Cosmic Tip: Your warmth attracts the right people today.",
        "Tips for singles: Say yes to the plan you almost declined.",
        "Tips for couples: Small gestures carry big weight today."
      ]
    }
  }
}
```

## What's in a prediction?

Every prediction response is structured the same way across all four Western endpoints (daily / weekly / monthly / yearly), so you can build one UI and reuse it. The `data.prediction` object contains:

- **`personal`** : how relationships, home life and personal growth look for the period
- **`health`** : physical wellness, energy levels, lifestyle recommendations
- **`profession`** : career, projects, workplace dynamics
- **`emotions`** : mood patterns, emotional themes, inner work
- **`travel`** : travel outlook, whether short trips or long journeys are favoured
- **`luck`** : an array of 4-6 short strings with colors, lucky numbers, alphabets, cosmic tips, and advice for singles/couples

Because the schema is identical across cadences, one React/Vue component can render any of the four endpoints with the cadence as a prop.

---

## Code examples

### cURL

```bash
curl -X POST "https://astroapi-5.divineapi.com/api/v5/daily-horoscope" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  --data-urlencode "api_key=YOUR_API_KEY" \
  --data-urlencode "sign=leo" \
  --data-urlencode "h_day=today" \
  --data-urlencode "tzone=5.5"
```

### Python (requests)

```python
import requests

url = "https://astroapi-5.divineapi.com/api/v5/daily-horoscope"

headers = {
    "Authorization": "Bearer YOUR_API_KEY",
    "Content-Type": "application/x-www-form-urlencoded",
}

payload = {
    "api_key": "YOUR_API_KEY",
    "sign":    "leo",
    "h_day":   "today",
    "tzone":   5.5,
}

response = requests.post(url, headers=headers, data=payload)
print(response.json()["data"]["prediction"]["personal"])
```

### JavaScript (browser, fetch)

```javascript
const url = "https://astroapi-5.divineapi.com/api/v5/daily-horoscope";

const body = new URLSearchParams({
  api_key: "YOUR_API_KEY",
  sign:    "leo",
  h_day:   "today",
  tzone:   5.5,
});

const res = await fetch(url, {
  method: "POST",
  headers: {
    "Authorization": "Bearer YOUR_API_KEY",
    "Content-Type":  "application/x-www-form-urlencoded",
  },
  body,
});

const { data } = await res.json();
document.getElementById("horoscope").textContent = data.prediction.personal;
```

### Node.js (fetch, Node 18+)

```javascript
// Node.js 18+ ships with fetch built-in, no dependencies needed.

async function getDailyHoroscope(sign) {
  const url = "https://astroapi-5.divineapi.com/api/v5/daily-horoscope";

  const body = new URLSearchParams({
    api_key: "YOUR_API_KEY",
    sign,
    h_day:   "today",
    tzone:   5.5,
  });

  const res = await fetch(url, {
    method: "POST",
    headers: {
      "Authorization": "Bearer YOUR_API_KEY",
      "Content-Type":  "application/x-www-form-urlencoded",
    },
    body,
  });

  return res.json();
}

const horoscope = await getDailyHoroscope("leo");
console.log(horoscope.data.prediction);
```

### PHP (curl)

```php
<?php
$url = "https://astroapi-5.divineapi.com/api/v5/daily-horoscope";

$payload = http_build_query([
    "api_key" => "YOUR_API_KEY",
    "sign"    => "leo",
    "h_day"   => "today",
    "tzone"   => 5.5,
]);

$ch = curl_init($url);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $payload);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    "Authorization: Bearer YOUR_API_KEY",
    "Content-Type: application/x-www-form-urlencoded",
]);

$response = json_decode(curl_exec($ch), true);
curl_close($ch);

echo $response["data"]["prediction"]["personal"];
```

### Go (net/http)

```go
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"
    "net/url"
    "strings"
)

type Response struct {
    Success int `json:"success"`
    Data    struct {
        Sign       string `json:"sign"`
        Date       string `json:"date"`
        Prediction struct {
            Personal   string   `json:"personal"`
            Health     string   `json:"health"`
            Profession string   `json:"profession"`
            Emotions   string   `json:"emotions"`
            Travel     string   `json:"travel"`
            Luck       []string `json:"luck"`
        } `json:"prediction"`
    } `json:"data"`
}

func main() {
    endpoint := "https://astroapi-5.divineapi.com/api/v5/daily-horoscope"

    form := url.Values{}
    form.Set("api_key", "YOUR_API_KEY")
    form.Set("sign",    "leo")
    form.Set("h_day",   "today")
    form.Set("tzone",   "5.5")

    req, _ := http.NewRequest("POST", endpoint, strings.NewReader(form.Encode()))
    req.Header.Set("Authorization", "Bearer YOUR_API_KEY")
    req.Header.Set("Content-Type",  "application/x-www-form-urlencoded")

    resp, err := http.DefaultClient.Do(req)
    if err != nil {
        panic(err)
    }
    defer resp.Body.Close()

    body, _ := io.ReadAll(resp.Body)
    var r Response
    json.Unmarshal(body, &r)
    fmt.Println(r.Data.Prediction.Personal)
}
```

---

## FAQ

**How often do predictions update?**
Daily predictions change once per day (anchored to the `tzone` you pass). Weekly predictions change once per week, monthly once per month, yearly once per year. Two calls on the same day with the same `(sign, tzone, lan)` tuple return the same content, so responses are safe to cache.

**Can I cache responses on my side?**
Yes, and you should. A CDN or edge cache keyed by `(endpoint, sign, h_day, tzone, lan)` will hit DivineAPI roughly once per bucket and serve the rest from your own cache. For daily: cache until next midnight in the user's timezone.

**What zodiac signs are supported?**
All 12 Western tropical signs for daily/weekly/monthly/yearly. The Chinese Horoscope endpoint derives the zodiac animal from a birth year, so no sign is required there.

**What languages does the API support?**
25 languages, requested via the `lan` parameter. English is the default. Full language code table is on the [docs site](https://developers.divineapi.com/divine-api/understanding-time-zones-a-comprehensive-guide).

**What's the difference between Chinese Horoscope and the other horoscope endpoints?**
The four Western endpoints (daily/weekly/monthly/yearly) take a tropical zodiac `sign` and a cadence. The Chinese Horoscope endpoint takes a birth year (and period), internally maps the year to a Chinese zodiac animal (Rat, Ox, Tiger, ...), then returns guidance for that animal.

**Is the data authentic?**
Predictions are written by professional astrologers and updated continuously. The endpoints are not generated by a simple keyword shuffle: each period's content is fresh and themed.

---

## Other APIs by DivineAPI

[![Astrology API (hub)](https://img.shields.io/badge/Astrology%20API%20(hub)-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/astrology-api)
[![Kundali API](https://img.shields.io/badge/Kundali%20API-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/kundali-api)
[![Birth Chart API](https://img.shields.io/badge/Birth%20Chart%20API-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/birth-chart-api)
[![Panchang API](https://img.shields.io/badge/Panchang%20API-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/panchang-api)
[![Numerology API](https://img.shields.io/badge/Numerology%20API-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/numerology-api)
[![Hindu Festival API](https://img.shields.io/badge/Hindu%20Festival%20API-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/hindu-festival-api)
[![Daily Tarot](https://img.shields.io/badge/Daily%20Tarot-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/daily-tarot)
[![Yes or No Tarot](https://img.shields.io/badge/Yes%20or%20No%20Tarot-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/yes-or-no-tarot)
[![Fortune Cookie](https://img.shields.io/badge/Fortune%20Cookie-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/fortune-cookie)
[![Coffee Cup Reading](https://img.shields.io/badge/Coffee%20Cup%20Reading-cb22e6?style=for-the-badge&logoColor=white)](https://github.com/DivineAPI/coffee-cup-reading)

---

## Resources

- **Full documentation** → [developers.divineapi.com/horoscope-and-tarot-api](https://developers.divineapi.com/horoscope-and-tarot-api)
- **Parent platform README** → [github.com/DivineAPI/astrology-api](https://github.com/DivineAPI/astrology-api)
- **API status** → [status.divineapi.com](https://status.divineapi.com)
- **Postman collection** → [Run in Postman](https://documenter.getpostman.com/view/26759678/2sBXitCnDX)
- **Changelog** → [developers.divineapi.com/changelog](https://developers.divineapi.com/changelog)
- **Support** → [admin@divineapi.com](mailto:admin@divineapi.com)

---

## License & Usage

Code samples on this page are free to copy into your own projects, no attribution required. Marketing copy, logos, and the **DivineAPI** name are © 2026 DivineAPI, all rights reserved.

For the terms that govern the API service itself, see [divineapi.com/terms](https://divineapi.com/terms).

## Contact

Questions, feature requests or partnership enquiries → **[admin@divineapi.com](mailto:admin@divineapi.com)**
