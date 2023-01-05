---
title: Examples of Site Analytics Tags
description:
date: 2021-11-01
tags:
  - web analytics
layout: layouts/post.njk
---

## Comparison of the tracking tags in a few public sites
Javascript code for monitoring site traffic is  often placed in the very top of the html of a page. But it can be placed in the very bottom too. Here are the short tracking scripts I found in the html of some public sites.

### Government website: The NOAA Weather page
From `<head>` at the top of the homepage of weather.gov

```html
<script type="text/javascript" id="_fed_an_ua_tag" src="https://dap.digitalgov.gov/Universal-Federated-Analytics-Min.js?agency=DOC&subagency=NOAA">
</script>  

<script type="text/javascript">
    // GoogleAnalyticsObject is defined in the federated analytics script, but PUA option not used as forecast UA needs sampleRate
    window[window['GoogleAnalyticsObject']]('create', 'UA-40768555-1', 'weather.gov', {'sampleRate': 6});
    window[window['GoogleAnalyticsObject']]('set', 'anonymizeIp', true);
    window[window['GoogleAnalyticsObject']]('require', 'linkid');
    window[window['GoogleAnalyticsObject']]('send', 'pageview');
</script>
```

### CSS Tricks
Chris Coyer is of course an expert in best practices. And he prefers to put the tracking script way down at the end of `<body>` at the bottom of the csstricks.com homepage.

```html

<!-- WORDPRESS CLICKTRACKER -->
<script src='https://stats.wp.com/e-202144.js' defer>
</script>

<script>
	_stq = window._stq || [];
	_stq.push([ 'view', {v:'ext',j:'1:10.2.1',blog:'45537868',post:'0',tz:'-7',srv:'css-tricks.com'} ]);
	_stq.push([ 'clickTrackerInit', '45537868', '0' ]);
</script>

<script>
    window.activeMember = false;
  </script>

  <!-- GOOGLE ANALYTICS -->
  <script src="https://css-tricks.com/wp-content/themes/CSS-Tricks-19/js/min/global-concat.min.js?cache_bust=1634138996784"></script>
  
  <script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
  ga('create', 'UA-68528-29', 'auto');

  if (typeof articleYear !== "undefined") {
    ga('set', 'dimension1', articleYear);
  }
  if (typeof articleAuthor !== "undefined") {
    ga('set', 'dimension2', articleAuthor);
  }
  if (typeof articleType !== "undefined") {
    ga('set', 'dimension3', articleType);
  }

  ga('send', 'pageview');
</script>

<!-- CLOUDFLARE INSIGHTS -->
<script src="//instant.page/5.1.0" type="module" integrity="sha384-by67kQnR+pyfy8yWP4kPO12fHKRLHZPfEsiSXR8u2IKcTdxD805MGUXBzVPnkLHw"></script><script defer src="https://static.cloudflareinsights.com/beacon.min.js" data-cf-beacon='{"rayId":"6a76743ac7a32cd1","token":"2863ac31b15c48f5b94bd8b0c38aba94","version":"2021.10.0","si":100}'>
</script>  

<script defer src="https://static.cloudflareinsights.com/beacon.min.js" data-cf-beacon='{"rayId":"6a76743abb832cd1","token":"2863ac31b15c48f5b94bd8b0c38aba94","version":"2021.10.0","si":100}'>
</script>
```

### French web site: Inter Radio
From `<head>` at the top of the  of the www.franceinter.fr homepage body

```html
<!-- Google Analytics -->
<script type="didomi/javascript" data-vendor="c:googleana-UHGQNGqD" async src="https://www.googletagmanager.com/gtag/js?id=UA-85892755-1" data-no-instant>
</script>  

<!-- End of global snippet: Please do not remove -->
<script type="didomi/javascript" data-vendor="c:googleana-UHGQNGqD" data-no-instant>
  var selector = 'ga-analytics';
  if (!document.querySelector(`#${selector}`)) {
    (function (i, s, o, g, r, a, m) {
      i['GoogleAnalyticsObject'] = r
      i[r] = i[r] || function () {
        (i[r].q = i[r].q || []).push(arguments)
      }
      i[r].l = 1 * new Date()
      a = s.createElement(o)
      m = s.getElementsByTagName(o)[0]
      a.async = 1
      a.src = g
      a.id = selector
      m.parentNode.insertBefore(a, m)
    })(window, document, 'script', 'https://www.google-analytics.com/analytics.js', 'ga')
    window.ga('create', 'UA-85892755-1', { 'cookieExpires':34164000 } )
  }
</script>
<!-- End Google Analytics -->

<!-- FB Pixel -->
<script type="didomi/javascript" data-vendor="c:facebook-hdWetQNa" data-no-instant>
 var selector = 'fb-pixel';
  if (!document.querySelector(`#${selector}`)) {
    (function (f, b, e, v, n, t, s) {
      if (f.fbq) return
      n = f.fbq = function () {
        n.callMethod ? n.callMethod.apply(n, arguments) : n.queue.push(arguments)
      }
      if (!f._fbq) f._fbq = n
      n.push = n
      n.loaded = !0
      n.version = '2.0'
      n.queue = []
      t = b.createElement(e)
      t.async = !0
      t.src = v
      t.id = selector
      s = b.getElementsByTagName(e)[0]
      s.parentNode.insertBefore(t, s)
    })(window, document, 'script', 'https://connect.facebook.net/en_US/fbevents.js')
    window.fbq('init', '250310205420402')
    window.fbq('track', 'PageView')
  }
</script>
<!-- End FB Pixel -->

<!-- FB sdk -->
<script type="didomi/javascript" data-vendor="c:facebookc-rgacRMQm" async defer crossorigin="anonymous" src="https://connect.facebook.net/fr_FR/sdk.js#xfbml=1&version=v10.0" nonce="5to948Oi"></script><!-- End FB sdk --><!-- Insta SDK --><script type="didomi/javascript" data-vendor="c:instagram-eHKnGamG" async src="//platform.instagram.com/en_US/embeds.js"></script><!-- End Insta SDK --><!-- Twitter SDK --><script type="didomi/javascript" data-vendor="c:twitter-rNGnjKz6" async src="https://platform.twitter.com/widgets.js" charset="utf-8">
</script>
<!-- End Twitter SDK -->

<!-- ABTasty -->
<script type="didomi/javascript" data-vendor="c:abtasty-wqU9gKVj" data-no-instant>
    var selector = '_abtasty';
    if (!document.querySelector(`#${selector}`)) {
        (function (i, s, o, g, r, a, m) {
            i[r] = i[r] || []
            i['abtiming'] = 1 * new Date()
            a = s.createElement(o)
            m = s.getElementsByTagName(o)[0]
            a.async = 1
            a.src = g
            m.parentNode.insertBefore(a, m)
        })(window, document, 'script', '//try.abtasty.com/5c062a8502ec3205fe550a3e95592027.js', '_abtasty')
    }
</script>
<!-- End ABTasty -->
```

### SciURLs
Browserling is a cross browser tester. Browserling has many free public tools. This is from their sciruls.com homepage.
```html
    <!-- StatCounter -->
    <script type="text/javascript">
        var sc_project   = 11918814;
        var sc_invisible = 1; 
        var sc_security  = "5a4da49a";
    </script>
    <script async src="https://secure.statcounter.com/counter/counter.js">
    </script>  

    <!-- Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=UA-130230250-3"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag() { dataLayer.push(arguments) };
        gtag("js", new Date());
        gtag("config", "UA-130230250-3");
    </script>
```

### A high traffic journal, aimed at academia: Nature  
From <head> at the top of the nature.com homepage  

```html
  <script data-test="dataLayer">
        dataLayer = [{"content":{"category":{"contentType":"research highlight","legacy":{"webtrendsPrimaryArticleType":"research highlights","webtrendsSubjectTerms":"brain","webtrendsContentCategory":null,"webtrendsContentCollection":null,"webtrendsContentGroup":"Nature","webtrendsContentGroupType":null,"webtrendsContentSubGroup":"Research Highlight"}},"article":{"doi":"10.1038/d41586-021-02942-4"},"attributes":{"cms":"core media","deliveryPlatform":"oscar","copyright":{"open":false,"legacy":{"webtrendsLicenceType":null}}},"contentInfo":{"authors":[],"publishedAt":1635465600,"publishedAtString":"2021-10-29","title":"How ‘sleep misperception’ fools people into thinking they don’t sleep","legacy":null,"publishedAtTime":null,"documentType":"aplusplus"},"journal":{"pcode":"nature","title":"nature","volume":null,"issue":null},"authorization":{"status":false},"features":[{"name":"furtherReadingSection","present":false}],"collection":null},"page":{"category":{"pageType":"article"},"attributes":{"template":"magazine mosaic","featureFlags":[{"name":"ab_test_highlight_supp_info","active":false},{"name":"nature-oa-paywall","active":true},{"name":"nature-onwards-journey","active":false}],"testGroup":null},"search":null},"privacy":{},"version":"1.0.0","product":null,"session":null,"user":null,"backHalfContent":false,"country":"US","hasBody":false,"uneditedManuscript":false}];
</script>

<script>
    (function(w,d,t) {
        function cc() {
            var h = w.location.hostname;
            if (h.indexOf('preview-www.nature.com') > -1) return;

            var e = d.createElement(t),
                s = d.getElementsByTagName(t)[0];

            if (h.indexOf('nature.com') > -1) {
                e.src = 'https://cdn.cookielaw.org/scripttemplates/otSDKStub.js';
                e.setAttribute('data-domain-script', '83f2c78a-6cbc-4d1a-9088-3f8e8c4c7460');
            } else {
                e.src = '/static/js/cookie-consent-es5-bundle.34a145d526.js';
                e.setAttribute('data-consent', h);
            }
            s.parentNode.insertBefore(e, s);
        }

        !!w.google_tag_manager ? cc() : window.addEventListener('gtm_loaded', function() {cc()});
    })(window,document,'script');
</script>  

<script>
    function OptanonWrapper() {
        window.dataLayer.push({event:'OneTrustGroupsUpdated'});
        document.activeElement.blur();
    }
</script>  
        
<script>
(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
        new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
    j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
    'https://www.googletagmanager.com/gtm.js?id='+i+dl;
    j.addEventListener('load', function() {
    var _ge = new CustomEvent('gtm_loaded', { bubbles: true });
    d.dispatchEvent(_ge);
    });

    f.parentNode.insertBefore(j,f);
})(window,document,'script','dataLayer','GTM-NWDMT9Q');
</script>
```

## A university org

This is at the top of `<head>` at scout.wisc.edu.

```html
<script>(function(i,s,o,g,r,a,m){i["GoogleAnalyticsObject"]=r;i[r]=i[r]||function(){(i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)})(window,document,"script","https://www.google-analytics.com/analytics.js","ga");ga("create", "UA-856016-3", {"cookieDomain":"auto"});ga("send", "pageview");</script>
```

## Amazon affiliate

Some sites track their traffic by just tracking their clickthrough to a paying affiliate. This is centslessbooks.com

```html

			<a
				class="audible-button"
				onclick="ga('send', 'event', 'Audible Click');"
				href="https://www.amazon.com/Audible-Free-Trial-Digital-Membership/dp/B00NB86OYE/?ref_=assoc_tag_ph_1485906643682&_encoding=UTF8&camp=1789&creative=9325&linkCode=pf4&tag=promocents-20&linkId=d050ea3033d623c41fe6d7f076af36c5"
			>
```

## Tealium 1

This is in `<body>`, near its top, at ecommerce.tealiumdemo.com. Not sure why they put it there.

```html
<body class=" cms-page-view cms-training">
    
    <!-- Tealium Universal Data Object / Data Layer -->
<script type="text/javascript">
    utag_data = {"site_region":"en_US","site_currency":"USD","page_name":"training","page_type":"cms page","tealium_event":"page_view","bdid":"tT5HDcMra5Qb5zr9"};
</script>
<!-- ****************************************** --><!-- Async Load of Tealium utag.js library -->
<script type="text/javascript">
        (function(a,b,c,d){
            a='//tags.tiqcdn.com/utag/tealiumlabs/commerce/prod/utag.js';
        b=document;c='script';d=b.createElement(c);d.src=a;d.type='text/java'+c;d. 
        async=true;
        a=b.getElementsByTagName(c)[0];a.parentNode.insertBefore(d,a);
        })();
</script>
```

## Tealium 2

This is in `<head>` at tealium.com.

```html
    <script src="//tags.tiqcdn.com/utag/tealium/main/prod/utag.sync.js"></script>
```

And nearby, I think this is inserted when the page gets built. It is a tracker for the div that shows the newest blog post.
```html
<script type="text/javascript">
var utag_data = {
    "site_name": "Tealium",
    "site_description": "Customer Data Hub | Customer Data Platform and Tag Management",
    "page_type": "page",
    "post_id": 39341,
    "post_title": "Homepage",
    "post_author": "shawnpeters93",
    "post_date": "2021\/07\/08",
    "user_role": "guest"
};
</script>
```


This is in `<body>`, near its top, at tealium.com. Again, not sure why they put it there.

```html
<body class="home page-template page-template-jasper page-template-template-default page-template-jaspertemplate-default-php page page-id-39341 wpb-js-composer js-comp-ver-6.0.5 vc_responsive">

<!-- Loading script asynchronously -->
<script type="text/javascript">
 (function(a,b,c,d){
 a='//tags.tiqcdn.com/utag/tealium/main/prod/utag.js';
 b=document;c='script';d=b.createElement(c);d.src=a;d.type='text/java'+c;d.async=true;
 a=b.getElementsByTagName(c)[0];a.parentNode.insertBefore(d,a);
 })();
</script>
<!-- END: T-WP -->
```








## Tealium 3
This is a pair of utag scripts near line 70 of community.tealiumiq.com homepage

```html
<script type="text/javascript">
var utag_data = {tealium_event:"page_view"};
utag_data['is_logged_in'] = "0";
utag_data['page_type'] = "section";
</script>

<!-- //DO NOT TOUCH THIS -->
<!-- Loading script asynchronously -->
<script type="text/javascript">
    (function(a,b,c,d){
    a='//tags.tiqcdn.com/utag/tealium/community/prod/utag.js';
    b=document;c='script';d=b.createElement(c);d.src=a;d.type='text/java'+c;d.async=true;
    a=b.getElementsByTagName(c)[0];a.parentNode.insertBefore(d,a);
    })();
</script>

```

And, from the same page, this is a one liner from near the top of `head` at community.tealiumiq.com/

** THIS IS 400 LINES LONG **

```js
(window.NREUM || (NREUM = {})).init = {
    ajax: {
        deny_list: [ "bam-cell.nr-data.net" ]
    }
};

(window.NREUM || (NREUM = {})).loader_config = {
    licenseKey: "90ec53e80f",
    applicationID: "376143191"
};

window.NREUM || (NREUM = {}), __nr_require = function(t, e, n) {
    function r(n) {
        if (!e[n]) {
            var i = e[n] = {
                exports: {}
            };
            t[n][0].call(i.exports, function(e) {
                var i = t[n][1][e];
                return r(i || e);
            }, i, i.exports);
        }
        return e[n].exports;
    }
    if ("function" == typeof __nr_require) return __nr_require;
    for (var i = 0; i < n.length; i++) r(n[i]);
    return r;
}({
    1: [ function(t, e, n) {
        function r() {}
        function i(t, e, n) {
            return function() {
                return o(t, [ u.now() ].concat(f(arguments)), e ? null : this, n), e ? void 0 : this;
            };
        }
        var o = t("handle"), a = t(8), f = t(9), c = t("ee").get("tracer"), u = t("loader"), s = NREUM;
        "undefined" == typeof window.newrelic && (newrelic = s);
        var d = [ "setPageViewName", "setCustomAttribute", "setErrorHandler", "finished", "addToTrace", "inlineHit", "addRelease" ], p = "api-", l = p + "ixn-";
        a(d, function(t, e) {
            s[e] = i(p + e, !0, "api");
        }), s.addPageAction = i(p + "addPageAction", !0), s.setCurrentRouteName = i(p + "routeName", !0), 
        e.exports = newrelic, s.interaction = function() {
            return new r().get();
        };
        var m = r.prototype = {
            createTracer: function(t, e) {
                var n = {}, r = this, i = "function" == typeof e;
                return o(l + "tracer", [ u.now(), t, n ], r), function() {
                    if (c.emit((i ? "" : "no-") + "fn-start", [ u.now(), r, i ], n), i) try {
                        return e.apply(this, arguments);
                    } catch (t) {
                        throw c.emit("fn-err", [ arguments, this, t ], n), t;
                    } finally {
                        c.emit("fn-end", [ u.now() ], n);
                    }
                };
            }
        };
        a("actionText,setName,setAttribute,save,ignore,onEnd,getContext,end,get".split(","), function(t, e) {
            m[e] = i(l + e);
        }), newrelic.noticeError = function(t, e) {
            "string" == typeof t && (t = new Error(t)), o("err", [ t, u.now(), !1, e ]);
        };
    }, {} ],
    2: [ function(t, e, n) {
        function r(t) {
            if (NREUM.init) {
                for (var e = NREUM.init, n = t.split("."), r = 0; r < n.length - 1; r++) if (e = e[n[r]], 
                "object" != typeof e) return;
                return e = e[n[n.length - 1]];
            }
        }
        e.exports = {
            getConfiguration: r
        };
    }, {} ],
    3: [ function(t, e, n) {
        function r() {
            return f.exists && performance.now ? Math.round(performance.now()) : (o = Math.max(new Date().getTime(), o)) - a;
        }
        function i() {
            return o;
        }
        var o = new Date().getTime(), a = o, f = t(10);
        e.exports = r, e.exports.offset = a, e.exports.getLastTimestamp = i;
    }, {} ],
    4: [ function(t, e, n) {
        function r(t) {
            return !(!t || !t.protocol || "file:" === t.protocol);
        }
        e.exports = r;
    }, {} ],
    5: [ function(t, e, n) {
        function r(t, e) {
            var n = t.getEntries();
            n.forEach(function(t) {
                "first-paint" === t.name ? d("timing", [ "fp", Math.floor(t.startTime) ]) : "first-contentful-paint" === t.name && d("timing", [ "fcp", Math.floor(t.startTime) ]);
            });
        }
        function i(t, e) {
            var n = t.getEntries();
            n.length > 0 && d("lcp", [ n[n.length - 1] ]);
        }
        function o(t) {
            t.getEntries().forEach(function(t) {
                t.hadRecentInput || d("cls", [ t ]);
            });
        }
        function a(t) {
            if (t instanceof m && !g) {
                var e = Math.round(t.timeStamp), n = {
                    type: t.type
                };
                e <= p.now() ? n.fid = p.now() - e : e > p.offset && e <= Date.now() ? (e -= p.offset, 
                n.fid = p.now() - e) : e = p.now(), g = !0, d("timing", [ "fi", e, n ]);
            }
        }
        function f(t) {
            "hidden" === t && d("pageHide", [ p.now() ]);
        }
        if (!("init" in NREUM && "page_view_timing" in NREUM.init && "enabled" in NREUM.init.page_view_timing && NREUM.init.page_view_timing.enabled === !1)) {
            var c, u, s, d = t("handle"), p = t("loader"), l = t(7), m = NREUM.o.EV;
            if ("PerformanceObserver" in window && "function" == typeof window.PerformanceObserver) {
                c = new PerformanceObserver(r);
                try {
                    c.observe({
                        entryTypes: [ "paint" ]
                    });
                } catch (v) {}
                u = new PerformanceObserver(i);
                try {
                    u.observe({
                        entryTypes: [ "largest-contentful-paint" ]
                    });
                } catch (v) {}
                s = new PerformanceObserver(o);
                try {
                    s.observe({
                        type: "layout-shift",
                        buffered: !0
                    });
                } catch (v) {}
            }
            if ("addEventListener" in document) {
                var g = !1, h = [ "click", "keydown", "mousedown", "pointerdown", "touchstart" ];
                h.forEach(function(t) {
                    document.addEventListener(t, a, !1);
                });
            }
            l(f);
        }
    }, {} ],
    6: [ function(t, e, n) {
        function r(t, e) {
            if (!i) return !1;
            if (t !== i) return !1;
            if (!e) return !0;
            if (!o) return !1;
            for (var n = o.split("."), r = e.split("."), a = 0; a < r.length; a++) if (r[a] !== n[a]) return !1;
            return !0;
        }
        var i = null, o = null, a = /Version\/(\S+)\s+Safari/;
        if (navigator.userAgent) {
            var f = navigator.userAgent, c = f.match(a);
            c && f.indexOf("Chrome") === -1 && f.indexOf("Chromium") === -1 && (i = "Safari", 
            o = c[1]);
        }
        e.exports = {
            agent: i,
            version: o,
            match: r
        };
    }, {} ],
    7: [ function(t, e, n) {
        function r(t) {
            function e() {
                t(a && document[a] ? document[a] : document[i] ? "hidden" : "visible");
            }
            "addEventListener" in document && o && document.addEventListener(o, e, !1);
        }
        e.exports = r;
        var i, o, a;
        "undefined" != typeof document.hidden ? (i = "hidden", o = "visibilitychange", a = "visibilityState") : "undefined" != typeof document.msHidden ? (i = "msHidden", 
        o = "msvisibilitychange") : "undefined" != typeof document.webkitHidden && (i = "webkitHidden", 
        o = "webkitvisibilitychange", a = "webkitVisibilityState");
    }, {} ],
    8: [ function(t, e, n) {
        function r(t, e) {
            var n = [], r = "", o = 0;
            for (r in t) i.call(t, r) && (n[o] = e(r, t[r]), o += 1);
            return n;
        }
        var i = Object.prototype.hasOwnProperty;
        e.exports = r;
    }, {} ],
    9: [ function(t, e, n) {
        function r(t, e, n) {
            e || (e = 0), "undefined" == typeof n && (n = t ? t.length : 0);
            for (var r = -1, i = n - e || 0, o = Array(i < 0 ? 0 : i); ++r < i; ) o[r] = t[e + r];
            return o;
        }
        e.exports = r;
    }, {} ],
    10: [ function(t, e, n) {
        e.exports = {
            exists: "undefined" != typeof window.performance && window.performance.timing && "undefined" != typeof window.performance.timing.navigationStart
        };
    }, {} ],
    ee: [ function(t, e, n) {
        function r() {}
        function i(t) {
            function e(t) {
                return t && t instanceof r ? t : t ? u(t, c, a) : a();
            }
            function n(n, r, i, o, a) {
                if (a !== !1 && (a = !0), !l.aborted || o) {
                    t && a && t(n, r, i);
                    for (var f = e(i), c = v(n), u = c.length, s = 0; s < u; s++) c[s].apply(f, r);
                    var p = d[w[n]];
                    return p && p.push([ b, n, r, f ]), f;
                }
            }
            function o(t, e) {
                y[t] = v(t).concat(e);
            }
            function m(t, e) {
                var n = y[t];
                if (n) for (var r = 0; r < n.length; r++) n[r] === e && n.splice(r, 1);
            }
            function v(t) {
                return y[t] || [];
            }
            function g(t) {
                return p[t] = p[t] || i(n);
            }
            function h(t, e) {
                l.aborted || s(t, function(t, n) {
                    e = e || "feature", w[n] = e, e in d || (d[e] = []);
                });
            }
            var y = {}, w = {}, b = {
                on: o,
                addEventListener: o,
                removeEventListener: m,
                emit: n,
                get: g,
                listeners: v,
                context: e,
                buffer: h,
                abort: f,
                aborted: !1
            };
            return b;
        }
        function o(t) {
            return u(t, c, a);
        }
        function a() {
            return new r();
        }
        function f() {
            (d.api || d.feature) && (l.aborted = !0, d = l.backlog = {});
        }
        var c = "nr@context", u = t("gos"), s = t(8), d = {}, p = {}, l = e.exports = i();
        e.exports.getOrSetContext = o, l.backlog = d;
    }, {} ],
    gos: [ function(t, e, n) {
        function r(t, e, n) {
            if (i.call(t, e)) return t[e];
            var r = n();
            if (Object.defineProperty && Object.keys) try {
                return Object.defineProperty(t, e, {
                    value: r,
                    writable: !0,
                    enumerable: !1
                }), r;
            } catch (o) {}
            return t[e] = r, r;
        }
        var i = Object.prototype.hasOwnProperty;
        e.exports = r;
    }, {} ],
    handle: [ function(t, e, n) {
        function r(t, e, n, r) {
            i.buffer([ t ], r), i.emit(t, e, n);
        }
        var i = t("ee").get("handle");
        e.exports = r, r.ee = i;
    }, {} ],
    id: [ function(t, e, n) {
        function r(t) {
            var e = typeof t;
            return !t || "object" !== e && "function" !== e ? -1 : t === window ? 0 : a(t, o, function() {
                return i++;
            });
        }
        var i = 1, o = "nr@id", a = t("gos");
        e.exports = r;
    }, {} ],
    loader: [ function(t, e, n) {
        function r() {
            if (!R++) {
                var t = M.info = NREUM.info, e = v.getElementsByTagName("script")[0];
                if (setTimeout(u.abort, 3e4), !(t && t.licenseKey && t.applicationID && e)) return u.abort();
                c(E, function(e, n) {
                    t[e] || (t[e] = n);
                });
                var n = a();
                f("mark", [ "onload", n + M.offset ], null, "api"), f("timing", [ "load", n ]);
                var r = v.createElement("script");
                0 === t.agent.indexOf("http://") || 0 === t.agent.indexOf("https://") ? r.src = t.agent : r.src = l + "://" + t.agent, 
                e.parentNode.insertBefore(r, e);
            }
        }
        function i() {
            "complete" === v.readyState && o();
        }
        function o() {
            f("mark", [ "domContent", a() + M.offset ], null, "api");
        }
        var a = t(3), f = t("handle"), c = t(8), u = t("ee"), s = t(6), d = t(4), p = t(2), l = p.getConfiguration("ssl") === !1 ? "http" : "https", m = window, v = m.document, g = "addEventListener", h = "attachEvent", y = m.XMLHttpRequest, w = y && y.prototype, b = !d(m.location);
        NREUM.o = {
            ST: setTimeout,
            SI: m.setImmediate,
            CT: clearTimeout,
            XHR: y,
            REQ: m.Request,
            EV: m.Event,
            PR: m.Promise,
            MO: m.MutationObserver
        };
        var x = "" + location, E = {
            beacon: "bam.nr-data.net",
            errorBeacon: "bam.nr-data.net",
            agent: "js-agent.newrelic.com/nr-1211.min.js"
        }, O = y && w && w[g] && !/CriOS/.test(navigator.userAgent), M = e.exports = {
            offset: a.getLastTimestamp(),
            now: a,
            origin: x,
            features: {},
            xhrWrappable: O,
            userAgent: s,
            disabled: b
        };
        if (!b) {
            t(1), t(5), v[g] ? (v[g]("DOMContentLoaded", o, !1), m[g]("load", r, !1)) : (v[h]("onreadystatechange", i), 
            m[h]("onload", r)), f("mark", [ "firstbyte", a.getLastTimestamp() ], null, "api");
            var R = 0;
        }
    }, {} ],
    "wrap-function": [ function(t, e, n) {
        function r(t, e) {
            function n(e, n, r, c, u) {
                function nrWrapper() {
                    var o, a, s, p;
                    try {
                        a = this, o = d(arguments), s = "function" == typeof r ? r(o, a) : r || {};
                    } catch (l) {
                        i([ l, "", [ o, a, c ], s ], t);
                    }
                    f(n + "start", [ o, a, c ], s, u);
                    try {
                        return p = e.apply(a, o);
                    } catch (m) {
                        throw f(n + "err", [ o, a, m ], s, u), m;
                    } finally {
                        f(n + "end", [ o, a, p ], s, u);
                    }
                }
                return a(e) ? e : (n || (n = ""), nrWrapper[p] = e, o(e, nrWrapper, t), nrWrapper);
            }
            function r(t, e, r, i, o) {
                r || (r = "");
                var f, c, u, s = "-" === r.charAt(0);
                for (u = 0; u < e.length; u++) c = e[u], f = t[c], a(f) || (t[c] = n(f, s ? c + r : r, i, c, o));
            }
            function f(n, r, o, a) {
                if (!m || e) {
                    var f = m;
                    m = !0;
                    try {
                        t.emit(n, r, o, e, a);
                    } catch (c) {
                        i([ c, n, r, o ], t);
                    }
                    m = f;
                }
            }
            return t || (t = s), n.inPlace = r, n.flag = p, n;
        }
        function i(t, e) {
            e || (e = s);
            try {
                e.emit("internal-error", t);
            } catch (n) {}
        }
        function o(t, e, n) {
            if (Object.defineProperty && Object.keys) try {
                var r = Object.keys(t);
                return r.forEach(function(n) {
                    Object.defineProperty(e, n, {
                        get: function() {
                            return t[n];
                        },
                        set: function(e) {
                            return t[n] = e, e;
                        }
                    });
                }), e;
            } catch (o) {
                i([ o ], n);
            }
            for (var a in t) l.call(t, a) && (e[a] = t[a]);
            return e;
        }
        function a(t) {
            return !(t && t instanceof Function && t.apply && !t[p]);
        }
        function f(t, e) {
            var n = e(t);
            return n[p] = t, o(t, n, s), n;
        }
        function c(t, e, n) {
            var r = t[e];
            t[e] = f(r, n);
        }
        function u() {
            for (var t = arguments.length, e = new Array(t), n = 0; n < t; ++n) e[n] = arguments[n];
            return e;
        }
        var s = t("ee"), d = t(9), p = "nr@original", l = Object.prototype.hasOwnProperty, m = !1;
        e.exports = r, e.exports.wrapFunction = f, e.exports.wrapInPlace = c, e.exports.argsToArray = u;
    }, {} ]
}, {}, [ "loader" ]);
```

## Caveman style tracking

To check traffic manually, without analytics sites, try looking at the server's logs. These are stored wherever the Apache configuration says to store them.  Mine are usually at `/var/log/apache2/`. This is probably a dumb way for me to do it but I can *crudely* compare relative access frequency for my *pikl.me* and *tatll.me* sites:

```bash
evan@nodejs-nyc:~$ sudo tail -n 300 /var/log/apache2/access.log | grep pikl | wc
     10     211    2189
evan@nodejs-nyc:~$ sudo tail -n 300 /var/log/apache2/access.log | grep tatll | wc
      8     175    1980
```

