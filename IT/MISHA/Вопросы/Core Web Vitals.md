---
links:
  - https://habr.com/ru/companies/vk/articles/577792/
---
CWV — это подмножество метрик инициативы Web Vitals, позволяющих численно оценить впечатления пользователя от вашего сайта. Полученные с их помощью оценки пользовательского опыта применимы ко всем веб-страницам (независимо от их специализации), поэтому владельцам сайтов необходимо измерять CWV. Google планирует поддержать CWV во всех своих инструментах для разработчиков.

- TTFB: Time to First Byte
- FCP: First Contentful Paint
- FID: First Input Delay
- LCP: Largest Contentful Paint
- CLS: Cumulative Layout Shift
- INP: Interaction to Next Paint

### Бенчмарки:
- Lighthouse
- PageSpeed Insights
- WebPageTest

### `web-vitals@next`

- ﻿﻿🚧Core Web Vitals (CWV)
	- ﻿﻿FID
	- ﻿﻿LCP
	- ﻿﻿CLS ♾️ 👨‍🔬
- ﻿﻿⚠️ Other Web Vitals (OWV)
	- ﻿﻿FCP
	- ﻿﻿TTFB 🧪
	- ﻿﻿INP ♾️ 🧪
---
♾️ Следит за страницей
👨‍🔬 Перерабатывалась
🧪 В эксперименте

## TTFB: Time to First Byte
![[Pasted image 20240310142908.png]]
![[Pasted image 20240310143019.png]]
## FCP: First Contentful Paint
![[Pasted image 20240310143040.png]]
## FID: First Input Delay
![[Pasted image 20240310143112.png]]
![[Pasted image 20240310143142.png]]
## LCP: Largest Contentful Paint
![[Pasted image 20240310143155.png]]
## CLS: Cumulative Layout Shift
![[Pasted image 20240310143221.png]]
## INP: Interaction to Next Paint

![[Pasted image 20240310143334.png]]


![[Pasted image 20240310143416.png]]

## Рекомендации Google по улучшению CWV

Выделим основные советы Google по улучшению метрик CWV. Рядом с каждым советом мы добавили обозначения для десктопной версии главной страницы: 🟢 — уже реализовано, 🟡 — частично используется, 🔴 — не внедрено, ⚫️ — неприменимо (неактуально из-за специфики нашего проекта). Список рекомендаций:  
  

- [LCP](https://web.dev/optimize-lcp/):  
    - [Длительное время ответа сервера](https://web.dev/optimize-lcp/#slow-servers)  
        - [Оптимизируйте работу динамического SSR (Server-Side Rendering)](https://web.dev/optimize-lcp/#optimize-your-server) (в том числе серверных обращений за данными) — 🟡
        - [Направляйте пользователей в ближайшую CDN](https://web.dev/optimize-lcp/#route-users-to-a-nearby-cdn) (Content Delivery Network, сеть доставки и дистрибуции содержимого) — ⚫️
        - [Настройте кеширование статических файлов](https://web.dev/optimize-lcp/#cache-assets) (например, с помощью настройки заголовков ответов в [Nginx](https://www.nginx.com/)) — 🟢
        - [Используйте Service Worker для кеширования](https://web.dev/optimize-lcp/#serve-html-pages-cache-first) — 🔴
        - [Устанавливайте сторонние (third-party) подключения на раннем этапе](https://web.dev/optimize-lcp/#establish-third-party-connections-early)с помощью предзагрузки контента (специальных HTML-тегов) — 🟡
        - Используйте подписанные HTTP-обмены (Signed exchanges, SXGs) (актуально для сайтов, получающих наибольший трафик из результатов поиска Google) — ⚫️
    - [Блокировка рендеринга JavaScript и CSS](https://web.dev/optimize-lcp/#render-blocking-resources)  
        - [Уменьшение времени блокировки CSS](https://web.dev/optimize-lcp/#reduce-css-blocking-time)  
            - [Минифицируйте CSS](https://web.dev/optimize-lcp/#minify-css) — 🟢
            - [Отсрочьте загрузку некритического CSS](https://web.dev/defer-non-critical-css/) — ⚫️
            - [Используйте инлайнинг на страницу критического CSS](https://web.dev/optimize-lcp/#inline-critical-css) — 🔴
        - [Уменьшение времени блокировки JavaScript](https://web.dev/optimize-lcp/#reduce-javascript-blocking-time)  
            - Используйте все описанные выше техники для CSS (кроме отсрочивания загрузки некритичного JavaScript) — 🟡 
            - [Минимизируйте количество неиспользуемых полифилов](https://web.dev/serve-modern-code-to-modern-browsers/) — 🟡
    - [Медленная загрузка ресурсов](https://web.dev/optimize-lcp/#slow-resource-load-times)  
        - [Оптимизируйте и сжимайте изображения](https://web.dev/optimize-lcp/#optimize-and-compress-images) (кроме использования новейших форматов, таких как [WebP](https://developers.google.com/speed/webp)) — 🟡 
        - [Предварительно загружайте важные ресурсы](https://web.dev/optimize-lcp/#preload-important-resources) — 🟡
        - [Сжимайте текстовые файлы](https://web.dev/optimize-lcp/#compress-text-files) (например, используя [Gzip](https://www.youtube.com/watch?v=whGwm0Lky2s&feature=youtu.be&t=14m11s)) — 🟢
        - [Используйте адаптивную подачу](https://web.dev/optimize-lcp/#adaptive-serving) — ⚫️
        - [Кешируйте статические файлы с помощью Service Worker](https://web.dev/optimize-lcp/#cache-assets-using-a-service-worker) — 🔴
    - [Клиентский рендеринг](https://web.dev/optimize-lcp/#client-side-rendering)  
        - [Минимизируйте размер критического JavaScript](https://web.dev/optimize-lcp/#minimize-critical-javascript) — 🟡
        - [Используйте рендеринг на стороне сервера (SSR)](https://web.dev/optimize-lcp/#use-server-side-rendering) — 🔴
        - [Используйте предварительный рендеринг (pre-rendering)](https://web.dev/optimize-lcp/#use-pre-rendering) — ⚫️
- [FID](https://web.dev/optimize-fid/):  
    - Высокое влияние стороннего кода  
        - [Уменьшите влияние стороннего (third-party) кода](https://web.dev/third-party-summary/) — 🟡
    - [Долгое выполнение JavaScript](https://web.dev/bootup-time/)  
        - [Отправляйте только тот код, который нужен вашим пользователям, реализовав разделение кода](https://web.dev/reduce-javascript-payloads-with-code-splitting) (code splitting) — 🔴
        - [Минифицируйте и сожмите свой код](https://web.dev/reduce-network-payloads-using-text-compression) — 🟢
        - [Удалите неиспользуемый код](https://web.dev/remove-unused-code) — 🟡
        - [Уменьшите количество сетевых подключений за счет кеширования кода с помощью паттерна PRPL](https://web.dev/apply-instant-loading-with-prpl) — 🟡
    - [Минимизация работы основного потока](https://web.dev/mainthread-work-breakdown/)  
        - [Обработка скриптов](https://web.dev/mainthread-work-breakdown/#script-evaluation)  
            - [Оптимизируйте сторонний (third-party) JavaScript](https://web.dev/fast/#optimize-your-third-party-resources) — 🟢
            - [Используйте debounce в обработчиках ввода](https://developers.google.com/web/fundamentals/performance/rendering/debounce-your-input-handlers) — ⚫️
            - [Применяйте Web Workers](https://web.dev/off-main-thread/) — 🔴
        - [Стили и верстка](https://web.dev/mainthread-work-breakdown/#style-and-layout)  
            - [Уменьшите объем и сложность расчетов стилей](https://developers.google.com/web/fundamentals/performance/rendering/reduce-the-scope-and-complexity-of-style-calculations) — 🟢
            - [Избегайте больших, сложных макетов](https://developers.google.com/web/fundamentals/performance/rendering/avoid-large-complex-layouts-and-layout-thrashing?hl%3Dru&sa=D&source=editors&ust=1631606786869000&usg=AOvVaw0HTjG64tlkDd33-4bkrJAH) — 🟢
        - [Рендеринг](https://web.dev/mainthread-work-breakdown/#rendering)  
            - [Придерживайтесь только свойств композитора и управляйте количеством слоев](https://developers.google.com/web/fundamentals/performance/rendering/stick-to-compositor-only-properties-and-manage-layer-count) — 🟢
            - [Упростите сложную окраску и уменьшите площадь отрисовки](https://developers.google.com/web/fundamentals/performance/rendering/simplify-paint-complexity-and-reduce-paint-areas) — 🟢
        - [Парсинг HTML и CSS](https://web.dev/mainthread-work-breakdown/#parsing-html-and-css)  
            - [Извлеките и заинлайните критический CSS](https://web.dev/extract-critical-css/) — 🔴
            - [Минифицируйте CSS](https://web.dev/minify-css/) — 🟢
            - [Отложите загрузку некритического CSS](https://web.dev/defer-non-critical-css/) — ⚫️
        - [Разбор (парсинг) и выполнение скриптов](https://web.dev/mainthread-work-breakdown/#script-parsing-and-compilation) (схожие техники применяются в разделе «Долгое выполнение JavaScript» выше)  
            - [Отправляйте только тот код, который нужен вашим пользователям, реализовав разделение кода](https://web.dev/reduce-javascript-payloads-with-code-splitting/) (code splitting) — 🔴
            - [Удалите неиспользуемый код](https://web.dev/remove-unused-code) — 🟡
        - [Сборка мусора](https://web.dev/mainthread-work-breakdown/#garbage-collection) (Garbage collection)  
            - [Контролируйте общее использование памяти вашей веб-страницей](https://web.dev/monitor-total-page-memory-usage/) — 🟡
    - [Сохраняйте небольшое количество запросов и небольшие размеры отправляемых данных](https://web.dev/resource-summary/) — 🟢
- [CLS](https://web.dev/optimize-cls/):  
    - [Оптимизация загрузки изображений](https://web.dev/optimize-cls/#modern-best-practice)  
        - Используйте атрибуты изображений width и height для генерации CSS aspect-ratio — 🟡
        - Добавляйте атрибут srcset для отзывчивых изображений — 🟡
    - [Рекламные баннеры, встраиваемые объявления и окна iframe без предварительно известных размеров](https://web.dev/optimize-cls/#ads-embeds-and-iframes-without-dimensions)  
        - Статично зарезервируйте место для рекламного баннера — 🔴
        - Будьте осторожны, размещая не-sticky рекламу в верхней части области просмотра (избегайте сдвига всей страницы после асинхронной загрузки рекламного баннера) — ⚫️
        - Избегайте сворачивания зарезервированного под рекламу места, если рекламный баннер не приходит. Показывайте плейсхолдер — 🔴
        - Устраняйте сдвиги (shifts), зарезервировав максимально возможный размер возможной рекламы. Или выберите наиболее вероятный размер рекламного места на основе исторических данных — 🔴
    - [Динамически появляющийся контент](https://web.dev/optimize-cls/#dynamic-content)  
        - Избегайте вставки нового содержимого над существующим контентом, если только это не является ответом на взаимодействие с пользователем. Это гарантирует, что любые изменения макета будут ожидаемыми — 🟢
    - [Шрифты, вызывающие сдвиги](https://web.dev/optimize-cls/#web-fonts-causing-foutfoit)  
        - [Используйте font-display](https://web.dev/font-display/) — ⚫️
        - Применяйте [Font Loading API](https://web.dev/fast/#optimize-webfonts) для ускорения загрузки необходимых шрифтов — ⚫️
        - Используйте теги для предзагрузки — ⚫️
    - [Анимации](https://web.dev/optimize-cls/#animations)  
        - Отдавайте предпочтение transform-анимации свойств, запускающих изменение макета — 🟡