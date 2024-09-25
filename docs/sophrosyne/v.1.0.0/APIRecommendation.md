# Getting Started - Recommendation API

In this chapter you will learn how to use the Action Recommendations-API and trigger your Recommendations automatically by Alerts via REST.

## Recommendation-API Example

1. Get your Action Recommendation ID from the Action Recommendation Menu
2. Get an allowed Apikey from the Apikey Menu

your-domain:17609/api/v1/actionrecommendation/12b5cdea-e072-44a4-af2d-b9a56255373a/apikey/eyJhbGciOiJFUzI1NiJ9

## Integration Prometheus AlertManager

In your alertmanager.yaml cofig, enter the following entry:
```yaml
- name: Example-receiver
  webhook_configs:
  - url: 'http://127.0.0.1:17609/api/v1/actionrecommendation/9b77c78d-0002-4cf6-877e-c3f24e3677a8/apikey/eyJhbGciOiJFUzI1NiJ9'
    send_resolved: false
```

## Recommendation-API Specification

<!DOCTYPE html>
<html>

<head>
  <meta charset="utf8" />
  <title>Sophrosyne - Recommendation Service API</title>
  <!-- needed for adaptive design -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body {
      padding: 0;
      margin: 0;
    }
  </style>
  <script src="https://cdn.redoc.ly/redoc/v2.1.5/bundles/redoc.standalone.js"></script><style data-styled="true" data-styled-version="6.1.12">.htdgPt{width:calc(100% - 40%);padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.htdgPt{width:100%;padding:40px 40px;}}/*!sc*/
.gxopqJ{width:calc(100% - 40%);padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.gxopqJ{width:100%;padding:0px 40px;}}/*!sc*/
data-styled.g4[id="sc-fQpRED"]{content:"htdgPt,gxopqJ,"}/*!sc*/
.diwyyM{padding:40px 0;}/*!sc*/
.diwyyM:last-child{min-height:calc(100vh + 1px);}/*!sc*/
.diwyyM>.diwyyM:last-child{min-height:initial;}/*!sc*/
@media print,screen and (max-width: 75rem){.diwyyM{padding:0;}}/*!sc*/
.kcRA-dj{padding:40px 0;position:relative;}/*!sc*/
.kcRA-dj:last-child{min-height:calc(100vh + 1px);}/*!sc*/
.kcRA-dj>.kcRA-dj:last-child{min-height:initial;}/*!sc*/
@media print,screen and (max-width: 75rem){.kcRA-dj{padding:0;}}/*!sc*/
.kcRA-dj:not(:last-of-type):after{position:absolute;bottom:0;width:100%;display:block;content:'';border-bottom:1px solid rgba(0, 0, 0, 0.2);}/*!sc*/
data-styled.g5[id="sc-dsLQwm"]{content:"diwyyM,kcRA-dj,"}/*!sc*/
.fTxZsC{width:40%;color:#ffffff;background-color:#263238;padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.fTxZsC{width:100%;padding:40px 40px;}}/*!sc*/
data-styled.g6[id="sc-iKTcqh"]{content:"fTxZsC,"}/*!sc*/
.drGLlX{background-color:#263238;}/*!sc*/
data-styled.g7[id="sc-gnpbhQ"]{content:"drGLlX,"}/*!sc*/
.dSIRVR{display:flex;width:100%;padding:0;}/*!sc*/
@media print,screen and (max-width: 75rem){.dSIRVR{flex-direction:column;}}/*!sc*/
data-styled.g8[id="sc-la-DxNn"]{content:"dSIRVR,"}/*!sc*/
.gfRsnu{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#333333;}/*!sc*/
data-styled.g9[id="sc-iCZwEW"]{content:"gfRsnu,"}/*!sc*/
.cbpGTP{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;margin:0 0 20px;}/*!sc*/
data-styled.g10[id="sc-knesRu"]{content:"cbpGTP,"}/*!sc*/
.gwrByh{border-bottom:1px solid rgba(38, 50, 56, 0.3);margin:1em 0 1em 0;color:rgba(38, 50, 56, 0.5);font-weight:normal;text-transform:uppercase;font-size:0.929em;line-height:20px;}/*!sc*/
data-styled.g13[id="sc-dkjaqt"]{content:"gwrByh,"}/*!sc*/
.hSvuOo{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.hSvuOo:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
h1:hover>.hSvuOo::before,h2:hover>.hSvuOo::before,.hSvuOo:hover::before{visibility:visible;}/*!sc*/
data-styled.g14[id="sc-jCbFiK"]{content:"hSvuOo,"}/*!sc*/
.gUrACV{height:18px;width:18px;min-width:18px;vertical-align:middle;float:right;transition:transform 0.2s ease-out;transform:rotateZ(-90deg);}/*!sc*/
.iMxoRf{height:20px;width:20px;min-width:20px;vertical-align:middle;float:right;transition:transform 0.2s ease-out;transform:rotateZ(0);}/*!sc*/
.iMxoRf polygon{fill:white;}/*!sc*/
data-styled.g15[id="sc-cBYhjr"]{content:"gUrACV,iMxoRf,"}/*!sc*/
.gbdrVc{border-left:1px solid #7c7cbb;box-sizing:border-box;position:relative;padding:10px 10px 10px 0;}/*!sc*/
@media screen and (max-width: 50rem){.gbdrVc{display:block;overflow:hidden;}}/*!sc*/
tr:first-of-type>.gbdrVc,tr.last>.gbdrVc{border-left-width:0;background-position:top left;background-repeat:no-repeat;background-size:1px 100%;}/*!sc*/
tr:first-of-type>.gbdrVc{background-image:linear-gradient(
      to bottom,
      transparent 0%,
      transparent 22px,
      #7c7cbb 22px,
      #7c7cbb 100%
    );}/*!sc*/
tr.last>.gbdrVc{background-image:linear-gradient(
      to bottom,
      #7c7cbb 0%,
      #7c7cbb 22px,
      transparent 22px,
      transparent 100%
    );}/*!sc*/
tr.last+tr>.gbdrVc{border-left-color:transparent;}/*!sc*/
tr.last:first-child>.gbdrVc{background:none;border-left-color:transparent;}/*!sc*/
data-styled.g18[id="sc-tOkKi"]{content:"gbdrVc,"}/*!sc*/
.bUksBx{vertical-align:top;line-height:20px;white-space:nowrap;font-size:13px;font-family:Courier,monospace;}/*!sc*/
.bUksBx.deprecated{text-decoration:line-through;color:#707070;}/*!sc*/
data-styled.g20[id="sc-epPVmt"]{content:"bUksBx,"}/*!sc*/
.exGrJC{border-bottom:1px solid #9fb4be;padding:10px 0;width:75%;box-sizing:border-box;}/*!sc*/
tr.expanded .exGrJC{border-bottom:none;}/*!sc*/
@media screen and (max-width: 50rem){.exGrJC{padding:0 20px;border-bottom:none;border-left:1px solid #7c7cbb;}tr.last>.exGrJC{border-left:none;}}/*!sc*/
data-styled.g21[id="sc-fpSrms"]{content:"exGrJC,"}/*!sc*/
.hTjFRU{color:#7c7cbb;font-family:Courier,monospace;margin-right:10px;}/*!sc*/
.hTjFRU::before{content:'';display:inline-block;vertical-align:middle;width:10px;height:1px;background:#7c7cbb;}/*!sc*/
.hTjFRU::after{content:'';display:inline-block;vertical-align:middle;width:1px;background:#7c7cbb;height:7px;}/*!sc*/
data-styled.g22[id="sc-hfvVTD"]{content:"hTjFRU,"}/*!sc*/
.ceVHDP{border-collapse:separate;border-radius:3px;font-size:14px;border-spacing:0;width:100%;}/*!sc*/
.ceVHDP >tr{vertical-align:middle;}/*!sc*/
@media screen and (max-width: 50rem){.ceVHDP{display:block;}.ceVHDP >tr,.ceVHDP >tbody>tr{display:block;}}/*!sc*/
@media screen and (max-width: 50rem) and (-ms-high-contrast:none){.ceVHDP td{float:left;width:100%;}}/*!sc*/
.ceVHDP .sc-ifyrTC,.ceVHDP .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC,.ceVHDP .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC{margin:1em;margin-right:0;background:#fafafa;}/*!sc*/
.ceVHDP .sc-ifyrTC .sc-ifyrTC,.ceVHDP .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC,.ceVHDP .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC .sc-ifyrTC{background:#ffffff;}/*!sc*/
data-styled.g24[id="sc-dENhDJ"]{content:"ceVHDP,"}/*!sc*/
.fwfkcU code[class*='language-'],.fwfkcU pre[class*='language-']{text-shadow:0 -0.1em 0.2em black;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;}/*!sc*/
@media print{.fwfkcU code[class*='language-'],.fwfkcU pre[class*='language-']{text-shadow:none;}}/*!sc*/
.fwfkcU pre[class*='language-']{padding:1em;margin:0.5em 0;overflow:auto;}/*!sc*/
.fwfkcU .token.comment,.fwfkcU .token.prolog,.fwfkcU .token.doctype,.fwfkcU .token.cdata{color:hsl(30, 20%, 50%);}/*!sc*/
.fwfkcU .token.punctuation{opacity:0.7;}/*!sc*/
.fwfkcU .namespace{opacity:0.7;}/*!sc*/
.fwfkcU .token.property,.fwfkcU .token.tag,.fwfkcU .token.number,.fwfkcU .token.constant,.fwfkcU .token.symbol{color:#4a8bb3;}/*!sc*/
.fwfkcU .token.boolean{color:#e64441;}/*!sc*/
.fwfkcU .token.selector,.fwfkcU .token.attr-name,.fwfkcU .token.string,.fwfkcU .token.char,.fwfkcU .token.builtin,.fwfkcU .token.inserted{color:#a0fbaa;}/*!sc*/
.fwfkcU .token.selector+a,.fwfkcU .token.attr-name+a,.fwfkcU .token.string+a,.fwfkcU .token.char+a,.fwfkcU .token.builtin+a,.fwfkcU .token.inserted+a,.fwfkcU .token.selector+a:visited,.fwfkcU .token.attr-name+a:visited,.fwfkcU .token.string+a:visited,.fwfkcU .token.char+a:visited,.fwfkcU .token.builtin+a:visited,.fwfkcU .token.inserted+a:visited{color:#4ed2ba;text-decoration:underline;}/*!sc*/
.fwfkcU .token.property.string{color:white;}/*!sc*/
.fwfkcU .token.operator,.fwfkcU .token.entity,.fwfkcU .token.url,.fwfkcU .token.variable{color:hsl(40, 90%, 60%);}/*!sc*/
.fwfkcU .token.atrule,.fwfkcU .token.attr-value,.fwfkcU .token.keyword{color:hsl(350, 40%, 70%);}/*!sc*/
.fwfkcU .token.regex,.fwfkcU .token.important{color:#e90;}/*!sc*/
.fwfkcU .token.important,.fwfkcU .token.bold{font-weight:bold;}/*!sc*/
.fwfkcU .token.italic{font-style:italic;}/*!sc*/
.fwfkcU .token.entity{cursor:help;}/*!sc*/
.fwfkcU .token.deleted{color:red;}/*!sc*/
data-styled.g32[id="sc-euGpHm"]{content:"fwfkcU,"}/*!sc*/
.bWVgjU{position:relative;}/*!sc*/
data-styled.g37[id="sc-dJDBYC"]{content:"bWVgjU,"}/*!sc*/
.kqJXdD{font-family:Roboto,sans-serif;font-weight:400;line-height:1.5em;}/*!sc*/
.kqJXdD p:last-child{margin-bottom:0;}/*!sc*/
.kqJXdD h1{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#32329f;margin-top:0;}/*!sc*/
.kqJXdD h2{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;}/*!sc*/
.kqJXdD code{color:#e53935;background-color:rgba(38, 50, 56, 0.05);font-family:Courier,monospace;border-radius:2px;border:1px solid rgba(38, 50, 56, 0.1);padding:0 5px;font-size:13px;font-weight:400;word-break:break-word;}/*!sc*/
.kqJXdD pre{font-family:Courier,monospace;white-space:pre;background-color:#11171a;color:white;padding:20px;overflow-x:auto;line-height:normal;border-radius:0;border:1px solid rgba(38, 50, 56, 0.1);}/*!sc*/
.kqJXdD pre code{background-color:transparent;color:white;padding:0;}/*!sc*/
.kqJXdD pre code:before,.kqJXdD pre code:after{content:none;}/*!sc*/
.kqJXdD blockquote{margin:0;margin-bottom:1em;padding:0 15px;color:#777;border-left:4px solid #ddd;}/*!sc*/
.kqJXdD img{max-width:100%;box-sizing:content-box;}/*!sc*/
.kqJXdD ul,.kqJXdD ol{padding-left:2em;margin:0;margin-bottom:1em;}/*!sc*/
.kqJXdD ul ul,.kqJXdD ol ul,.kqJXdD ul ol,.kqJXdD ol ol{margin-bottom:0;margin-top:0;}/*!sc*/
.kqJXdD table{display:block;width:100%;overflow:auto;word-break:normal;word-break:keep-all;border-collapse:collapse;border-spacing:0;margin-top:1.5em;margin-bottom:1.5em;}/*!sc*/
.kqJXdD table tr{background-color:#fff;border-top:1px solid #ccc;}/*!sc*/
.kqJXdD table tr:nth-child(2n){background-color:#fafafa;}/*!sc*/
.kqJXdD table th,.kqJXdD table td{padding:6px 13px;border:1px solid #ddd;}/*!sc*/
.kqJXdD table th{text-align:left;font-weight:bold;}/*!sc*/
.kqJXdD .share-link{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.kqJXdD .share-link:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
.kqJXdD h1:hover>.share-link::before,.kqJXdD h2:hover>.share-link::before,.kqJXdD .share-link:hover::before{visibility:visible;}/*!sc*/
.kqJXdD a{text-decoration:auto;color:#32329f;}/*!sc*/
.kqJXdD a:visited{color:#32329f;}/*!sc*/
.kqJXdD a:hover{color:#6868cf;text-decoration:auto;}/*!sc*/
.jYGAQp{font-family:Roboto,sans-serif;font-weight:400;line-height:1.5em;}/*!sc*/
.jYGAQp p:last-child{margin-bottom:0;}/*!sc*/
.jYGAQp p:first-child{margin-top:0;}/*!sc*/
.jYGAQp p:last-child{margin-bottom:0;}/*!sc*/
.jYGAQp h1{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#32329f;margin-top:0;}/*!sc*/
.jYGAQp h2{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;}/*!sc*/
.jYGAQp code{color:#e53935;background-color:rgba(38, 50, 56, 0.05);font-family:Courier,monospace;border-radius:2px;border:1px solid rgba(38, 50, 56, 0.1);padding:0 5px;font-size:13px;font-weight:400;word-break:break-word;}/*!sc*/
.jYGAQp pre{font-family:Courier,monospace;white-space:pre;background-color:#11171a;color:white;padding:20px;overflow-x:auto;line-height:normal;border-radius:0;border:1px solid rgba(38, 50, 56, 0.1);}/*!sc*/
.jYGAQp pre code{background-color:transparent;color:white;padding:0;}/*!sc*/
.jYGAQp pre code:before,.jYGAQp pre code:after{content:none;}/*!sc*/
.jYGAQp blockquote{margin:0;margin-bottom:1em;padding:0 15px;color:#777;border-left:4px solid #ddd;}/*!sc*/
.jYGAQp img{max-width:100%;box-sizing:content-box;}/*!sc*/
.jYGAQp ul,.jYGAQp ol{padding-left:2em;margin:0;margin-bottom:1em;}/*!sc*/
.jYGAQp ul ul,.jYGAQp ol ul,.jYGAQp ul ol,.jYGAQp ol ol{margin-bottom:0;margin-top:0;}/*!sc*/
.jYGAQp table{display:block;width:100%;overflow:auto;word-break:normal;word-break:keep-all;border-collapse:collapse;border-spacing:0;margin-top:1.5em;margin-bottom:1.5em;}/*!sc*/
.jYGAQp table tr{background-color:#fff;border-top:1px solid #ccc;}/*!sc*/
.jYGAQp table tr:nth-child(2n){background-color:#fafafa;}/*!sc*/
.jYGAQp table th,.jYGAQp table td{padding:6px 13px;border:1px solid #ddd;}/*!sc*/
.jYGAQp table th{text-align:left;font-weight:bold;}/*!sc*/
.jYGAQp .share-link{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.jYGAQp .share-link:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
.jYGAQp h1:hover>.share-link::before,.jYGAQp h2:hover>.share-link::before,.jYGAQp .share-link:hover::before{visibility:visible;}/*!sc*/
.jYGAQp a{text-decoration:auto;color:#32329f;}/*!sc*/
.jYGAQp a:visited{color:#32329f;}/*!sc*/
.jYGAQp a:hover{color:#6868cf;text-decoration:auto;}/*!sc*/
data-styled.g42[id="sc-exayXG"]{content:"kqJXdD,jYGAQp,"}/*!sc*/
.dRdjww{display:inline;}/*!sc*/
data-styled.g43[id="sc-dHrNzZ"]{content:"dRdjww,"}/*!sc*/
.bJcEcT{vertical-align:middle;font-size:13px;line-height:20px;}/*!sc*/
data-styled.g58[id="sc-xuUkR"]{content:"bJcEcT,"}/*!sc*/
.kDPMlG{color:rgba(102,102,102,0.9);}/*!sc*/
data-styled.g59[id="sc-cvzDha"]{content:"kDPMlG,"}/*!sc*/
.etUsjc{color:#666;}/*!sc*/
data-styled.g60[id="sc-gKROGD"]{content:"etUsjc,"}/*!sc*/
.gLEAmN{color:#d41f1c;font-size:0.9em;font-weight:normal;margin-left:20px;line-height:1;}/*!sc*/
data-styled.g62[id="sc-hrDJJk"]{content:"gLEAmN,"}/*!sc*/
.edbYXQ{margin-top:0;margin-bottom:0.5em;}/*!sc*/
data-styled.g91[id="sc-gjHHYa"]{content:"edbYXQ,"}/*!sc*/
.cwcfQE{border:1px solid #32329f;color:#32329f;font-weight:normal;margin-left:0.5em;padding:4px 8px 4px;display:inline-block;text-decoration:none;cursor:pointer;}/*!sc*/
data-styled.g92[id="sc-kyZTxD"]{content:"cwcfQE,"}/*!sc*/
.QUyzu{width:9ex;display:inline-block;height:13px;line-height:13px;background-color:#333;border-radius:3px;background-repeat:no-repeat;background-position:6px 4px;font-size:7px;font-family:Verdana,sans-serif;color:white;text-transform:uppercase;text-align:center;font-weight:bold;vertical-align:middle;margin-right:6px;margin-top:2px;}/*!sc*/
.QUyzu.get{background-color:#2F8132;}/*!sc*/
.QUyzu.post{background-color:#186FAF;}/*!sc*/
.QUyzu.put{background-color:#95507c;}/*!sc*/
.QUyzu.options{background-color:#947014;}/*!sc*/
.QUyzu.patch{background-color:#bf581d;}/*!sc*/
.QUyzu.delete{background-color:#cc3333;}/*!sc*/
.QUyzu.basic{background-color:#707070;}/*!sc*/
.QUyzu.link{background-color:#07818F;}/*!sc*/
.QUyzu.head{background-color:#A23DAD;}/*!sc*/
.QUyzu.hook{background-color:#32329f;}/*!sc*/
.QUyzu.schema{background-color:#707070;}/*!sc*/
data-styled.g99[id="sc-exkVDC"]{content:"QUyzu,"}/*!sc*/
.hYtPsf{margin:0;padding:0;}/*!sc*/
.hYtPsf:first-child{padding-bottom:32px;}/*!sc*/
.sc-iMDhdf .sc-iMDhdf{font-size:0.929em;}/*!sc*/
.fEjWGm{margin:0;padding:0;display:none;}/*!sc*/
.fEjWGm:first-child{padding-bottom:32px;}/*!sc*/
.sc-iMDhdf .sc-iMDhdf{font-size:0.929em;}/*!sc*/
data-styled.g100[id="sc-iMDhdf"]{content:"hYtPsf,fEjWGm,"}/*!sc*/
.btrDvq{list-style:none inside none;overflow:hidden;text-overflow:ellipsis;padding:0;}/*!sc*/
data-styled.g101[id="sc-loAbOW"]{content:"btrDvq,"}/*!sc*/
.cwxKjr{cursor:pointer;color:#333333;margin:0;padding:12.5px 20px;display:flex;justify-content:space-between;font-family:Montserrat,sans-serif;font-size:0.929em;text-transform:none;background-color:#fafafa;}/*!sc*/
.cwxKjr:hover{color:#32329f;background-color:#e1e1e1;}/*!sc*/
.cwxKjr .sc-cBYhjr{height:1.5em;width:1.5em;}/*!sc*/
.cwxKjr .sc-cBYhjr polygon{fill:#333333;}/*!sc*/
.cmGsIR{cursor:pointer;color:#333333;margin:0;padding:12.5px 20px;display:flex;justify-content:space-between;font-family:Montserrat,sans-serif;background-color:#fafafa;}/*!sc*/
.cmGsIR:hover{color:#32329f;background-color:#ededed;}/*!sc*/
.cmGsIR .sc-cBYhjr{height:1.5em;width:1.5em;}/*!sc*/
.cmGsIR .sc-cBYhjr polygon{fill:#333333;}/*!sc*/
data-styled.g102[id="sc-bPZXsP"]{content:"cwxKjr,cmGsIR,"}/*!sc*/
.glMKqQ{display:inline-block;vertical-align:middle;width:calc(100% - 38px);overflow:hidden;text-overflow:ellipsis;}/*!sc*/
data-styled.g103[id="sc-eteQWc"]{content:"glMKqQ,"}/*!sc*/
.iljewH{font-size:0.8em;margin-top:10px;text-align:center;position:fixed;width:260px;bottom:0;background:#fafafa;}/*!sc*/
.iljewH a,.iljewH a:visited,.iljewH a:hover{color:#333333!important;padding:5px 0;border-top:1px solid #e1e1e1;text-decoration:none;display:flex;align-items:center;justify-content:center;}/*!sc*/
.iljewH img{width:15px;margin-right:5px;}/*!sc*/
@media screen and (max-width: 50rem){.iljewH{width:100%;}}/*!sc*/
data-styled.g104[id="sc-gkavYR"]{content:"iljewH,"}/*!sc*/
.dCbPd{cursor:pointer;position:relative;margin-bottom:5px;}/*!sc*/
data-styled.g110[id="sc-dKsqdn"]{content:"dCbPd,"}/*!sc*/
.jcAXWA{font-family:Courier,monospace;margin-left:10px;flex:1;overflow-x:hidden;text-overflow:ellipsis;}/*!sc*/
data-styled.g111[id="sc-eowDPD"]{content:"jcAXWA,"}/*!sc*/
.gsBSOU{outline:0;color:inherit;width:100%;text-align:left;cursor:pointer;padding:10px 30px 10px 20px;border-radius:4px 4px 0 0;background-color:#11171a;display:flex;white-space:nowrap;align-items:center;border:1px solid transparent;border-bottom:0;transition:border-color 0.25s ease;}/*!sc*/
.gsBSOU ..sc-eowDPD{color:#ffffff;}/*!sc*/
.gsBSOU:focus{box-shadow:inset 0 2px 2px rgba(0, 0, 0, 0.45),0 2px 0 rgba(128, 128, 128, 0.25);}/*!sc*/
data-styled.g112[id="sc-iAlELC"]{content:"gsBSOU,"}/*!sc*/
.kpMtuJ{font-size:0.929em;line-height:20px;background-color:#186FAF;color:#ffffff;padding:3px 10px;text-transform:uppercase;font-family:Montserrat,sans-serif;margin:0;}/*!sc*/
data-styled.g113[id="sc-oeqTF"]{content:"kpMtuJ,"}/*!sc*/
.bFiOkX{position:absolute;width:100%;z-index:100;background:#fafafa;color:#263238;box-sizing:border-box;box-shadow:0 0 6px rgba(0, 0, 0, 0.33);overflow:hidden;border-bottom-left-radius:4px;border-bottom-right-radius:4px;transition:all 0.25s ease;visibility:hidden;transform:translateY(-50%) scaleY(0);}/*!sc*/
data-styled.g114[id="sc-ezTrPE"]{content:"bFiOkX,"}/*!sc*/
.hdRKqQ{padding:10px;}/*!sc*/
data-styled.g115[id="sc-drnuxz"]{content:"hdRKqQ,"}/*!sc*/
.jpmGrk{padding:5px;border:1px solid #ccc;background:#fff;word-break:break-all;color:#32329f;}/*!sc*/
.jpmGrk >span{color:#333333;}/*!sc*/
data-styled.g116[id="sc-hDcvty"]{content:"jpmGrk,"}/*!sc*/
.dSgpsc{display:block;border:0;width:100%;text-align:left;padding:10px;border-radius:2px;margin-bottom:4px;line-height:1.5em;cursor:pointer;color:#1d8127;background-color:rgba(29,129,39,0.07);cursor:default;}/*!sc*/
.dSgpsc:focus{outline:auto #1d8127;}/*!sc*/
.dSgpsc::before{content:"—";font-weight:bold;width:1.5em;text-align:center;display:inline-block;vertical-align:top;}/*!sc*/
.dSgpsc:focus{outline:0;}/*!sc*/
.bEasFS{display:block;border:0;width:100%;text-align:left;padding:10px;border-radius:2px;margin-bottom:4px;line-height:1.5em;cursor:pointer;color:#d41f1c;background-color:rgba(212,31,28,0.07);cursor:default;}/*!sc*/
.bEasFS:focus{outline:auto #d41f1c;}/*!sc*/
.bEasFS::before{content:"—";font-weight:bold;width:1.5em;text-align:center;display:inline-block;vertical-align:top;}/*!sc*/
.bEasFS:focus{outline:0;}/*!sc*/
data-styled.g119[id="sc-giOWAb"]{content:"dSgpsc,bEasFS,"}/*!sc*/
.gXPvFO{vertical-align:top;}/*!sc*/
data-styled.g122[id="sc-catHVh"]{content:"gXPvFO,"}/*!sc*/
.dbBFCU{font-size:1.3em;padding:0.2em 0;margin:3em 0 1.1em;color:#333333;font-weight:normal;}/*!sc*/
data-styled.g123[id="sc-eiLgtK"]{content:"dbBFCU,"}/*!sc*/
.cQxXyG{margin-bottom:30px;}/*!sc*/
data-styled.g128[id="sc-fpJhiv"]{content:"cQxXyG,"}/*!sc*/
.jQQbBk{user-select:none;width:20px;height:20px;align-self:center;display:flex;flex-direction:column;color:#32329f;}/*!sc*/
data-styled.g129[id="sc-bQEQyQ"]{content:"jQQbBk,"}/*!sc*/
.ktzGvn{width:260px;background-color:#fafafa;overflow:hidden;display:flex;flex-direction:column;backface-visibility:hidden;height:100vh;position:sticky;position:-webkit-sticky;top:0;}/*!sc*/
@media screen and (max-width: 50rem){.ktzGvn{position:fixed;z-index:20;width:100%;background:#fafafa;display:none;}}/*!sc*/
@media print{.ktzGvn{display:none;}}/*!sc*/
data-styled.g130[id="sc-dUMaFF"]{content:"ktzGvn,"}/*!sc*/
.kEKeWg{outline:none;user-select:none;background-color:#f2f2f2;color:#32329f;display:none;cursor:pointer;position:fixed;right:20px;z-index:100;border-radius:50%;box-shadow:0 0 20px rgba(0, 0, 0, 0.3);bottom:44px;width:60px;height:60px;padding:0 20px;}/*!sc*/
@media screen and (max-width: 50rem){.kEKeWg{display:flex;}}/*!sc*/
.kEKeWg svg{color:#0065FB;}/*!sc*/
@media print{.kEKeWg{display:none;}}/*!sc*/
data-styled.g131[id="sc-elEJnV"]{content:"kEKeWg,"}/*!sc*/
.fabhKa{font-family:Roboto,sans-serif;font-size:14px;font-weight:400;line-height:1.5em;color:#333333;display:flex;position:relative;text-align:left;-webkit-font-smoothing:antialiased;font-smoothing:antialiased;text-rendering:optimizeSpeed!important;tap-highlight-color:rgba(0, 0, 0, 0);text-size-adjust:100%;}/*!sc*/
.fabhKa *{box-sizing:border-box;-webkit-tap-highlight-color:rgba(255, 255, 255, 0);}/*!sc*/
data-styled.g132[id="sc-ixtKjU"]{content:"fabhKa,"}/*!sc*/
.laenHu{z-index:1;position:relative;overflow:hidden;width:calc(100% - 260px);contain:layout;}/*!sc*/
@media print,screen and (max-width: 50rem){.laenHu{width:100%;}}/*!sc*/
data-styled.g133[id="sc-dKGrn"]{content:"laenHu,"}/*!sc*/
.bWkBKa{background:#263238;position:absolute;top:0;bottom:0;right:0;width:calc((100% - 260px) * 0.4);}/*!sc*/
@media print,screen and (max-width: 75rem){.bWkBKa{display:none;}}/*!sc*/
data-styled.g134[id="sc-epzHnm"]{content:"bWkBKa,"}/*!sc*/
.dcjLWY{padding:5px 0;}/*!sc*/
data-styled.g135[id="sc-dovzVR"]{content:"dcjLWY,"}/*!sc*/
.dlxCDf{width:calc(100% - 40px);box-sizing:border-box;margin:0 20px;padding:5px 10px 5px 20px;border:0;border-bottom:1px solid #e1e1e1;font-family:Roboto,sans-serif;font-weight:bold;font-size:13px;color:#333333;background-color:transparent;outline:none;}/*!sc*/
data-styled.g136[id="sc-hAkARQ"]{content:"dlxCDf,"}/*!sc*/
.fBvPoH{position:absolute;left:20px;height:1.8em;width:0.9em;}/*!sc*/
.fBvPoH path{fill:#333333;}/*!sc*/
data-styled.g137[id="sc-kvXgyf"]{content:"fBvPoH,"}/*!sc*/
</style>
  <link href="https://fonts.googleapis.com/css?family=Montserrat:300,400,700|Roboto:300,400,700" rel="stylesheet">
</head>

<body>
  
      <div id="redoc"><div class="sc-ixtKjU fabhKa redoc-wrap"><div class="sc-dUMaFF ktzGvn menu-content" style="top:0px;height:calc(100vh - 0px)"><div role="search" class="sc-dovzVR dcjLWY"><svg class="sc-kvXgyf fBvPoH search-icon" version="1.1" viewBox="0 0 1000 1000" x="0px" xmlns="http://www.w3.org/2000/svg" y="0px"><path d="M968.2,849.4L667.3,549c83.9-136.5,66.7-317.4-51.7-435.6C477.1-25,252.5-25,113.9,113.4c-138.5,138.3-138.5,362.6,0,501C219.2,730.1,413.2,743,547.6,666.5l301.9,301.4c43.6,43.6,76.9,14.9,104.2-12.4C981,928.3,1011.8,893,968.2,849.4z M524.5,522c-88.9,88.7-233,88.7-321.8,0c-88.9-88.7-88.9-232.6,0-321.3c88.9-88.7,233-88.7,321.8,0C613.4,289.4,613.4,433.3,524.5,522z"></path></svg><input placeholder="Search..." aria-label="Search" type="text" class="sc-hAkARQ dlxCDf search-input" value=""/></div><div class="sc-dJDBYC bWVgjU scrollbar-container undefined"><ul role="menu" class="sc-iMDhdf hYtPsf"><li tabindex="0" depth="1" data-item-id="tag/Recommendation-API" role="menuitem" class="sc-loAbOW btrDvq"><label class="sc-bPZXsP cwxKjr -depth1"><span width="calc(100% - 38px)" title="Recommendation API" class="sc-eteQWc glMKqQ">Recommendation API</span><svg class="sc-cBYhjr gUrACV" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></label><ul class="sc-iMDhdf fEjWGm"><li tabindex="0" depth="2" data-item-id="tag/Recommendation-API/operation/triggerActionRecommendationById" role="menuitem" class="sc-loAbOW btrDvq"><label class="sc-bPZXsP cmGsIR -depth2"><span type="post" class="sc-exkVDC QUyzu operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-eteQWc glMKqQ">Trigger an action recommendation by id</span></label></li><li tabindex="0" depth="2" data-item-id="tag/Recommendation-API/operation/stopActionRecommendationById" role="menuitem" class="sc-loAbOW btrDvq"><label class="sc-bPZXsP cmGsIR -depth2"><span type="post" class="sc-exkVDC QUyzu operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-eteQWc glMKqQ">Trigger an action recommendation by id</span></label></li></ul></li></ul><div class="sc-gkavYR iljewH"><a target="_blank" rel="noopener noreferrer" href="https://redocly.com/redoc/">API docs by Redocly</a></div></div></div><div class="sc-elEJnV kEKeWg"><div class="sc-bQEQyQ jQQbBk"><svg class="" style="transform:translate(2px, -4px) rotate(180deg);transition:transform 0.2s ease" viewBox="0 0 926.23699 573.74994" version="1.1" x="0px" y="0px" width="15" height="15"><g transform="translate(904.92214,-879.1482)"><path d="
          m -673.67664,1221.6502 -231.2455,-231.24803 55.6165,
          -55.627 c 30.5891,-30.59485 56.1806,-55.627 56.8701,-55.627 0.6894,
          0 79.8637,78.60862 175.9427,174.68583 l 174.6892,174.6858 174.6892,
          -174.6858 c 96.079,-96.07721 175.253196,-174.68583 175.942696,
          -174.68583 0.6895,0 26.281,25.03215 56.8701,
          55.627 l 55.6165,55.627 -231.245496,231.24803 c -127.185,127.1864
          -231.5279,231.248 -231.873,231.248 -0.3451,0 -104.688,
          -104.0616 -231.873,-231.248 z
        " fill="currentColor"></path></g></svg><svg class="" style="transform:translate(2px, 4px);transition:transform 0.2s ease" viewBox="0 0 926.23699 573.74994" version="1.1" x="0px" y="0px" width="15" height="15"><g transform="translate(904.92214,-879.1482)"><path d="
          m -673.67664,1221.6502 -231.2455,-231.24803 55.6165,
          -55.627 c 30.5891,-30.59485 56.1806,-55.627 56.8701,-55.627 0.6894,
          0 79.8637,78.60862 175.9427,174.68583 l 174.6892,174.6858 174.6892,
          -174.6858 c 96.079,-96.07721 175.253196,-174.68583 175.942696,
          -174.68583 0.6895,0 26.281,25.03215 56.8701,
          55.627 l 55.6165,55.627 -231.245496,231.24803 c -127.185,127.1864
          -231.5279,231.248 -231.873,231.248 -0.3451,0 -104.688,
          -104.0616 -231.873,-231.248 z
        " fill="currentColor"></path></g></svg></div></div><div class="sc-dKGrn laenHu api-content"><div class="sc-dsLQwm diwyyM"><div class="sc-la-DxNn dSIRVR"><div class="sc-fQpRED htdgPt api-info"><h1 class="sc-iCZwEW sc-gjHHYa gfRsnu edbYXQ">Sophrosyne - Recommendation Service API<!-- --> <span>(<!-- -->1.0.0<!-- -->)</span></h1><p>Download OpenAPI specification<!-- -->:<a download="openapi.json" target="_blank" class="sc-kyZTxD cwcfQE">Download</a></p><div class="sc-euGpHm sc-exayXG fwfkcU kqJXdD"></div><div data-role="redoc-summary" html="" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD"></div><div data-role="redoc-description" html="&lt;p&gt;This API document describes the available Sophrosyne Recommendation APIs:&lt;/p&gt;
&lt;ol&gt;
&lt;li&gt;Trigger a Action Recommendation&lt;/li&gt;
&lt;/ol&gt;
&lt;p&gt;Core component of all API - Requests is the Action Recommendation&amp;#39;s ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD"><p>This API document describes the available Sophrosyne Recommendation APIs:</p>
<ol>
<li>Trigger a Action Recommendation</li>
</ol>
<p>Core component of all API - Requests is the Action Recommendation&#39;s ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.</p>
</div></div></div></div><div id="tag/Recommendation-API" data-section-id="tag/Recommendation-API" class="sc-dsLQwm diwyyM"><div class="sc-la-DxNn dSIRVR"><div class="sc-fQpRED htdgPt"><h2 class="sc-knesRu cbpGTP"><a class="sc-jCbFiK hSvuOo" href="#tag/Recommendation-API" aria-label="tag/Recommendation-API"></a>Recommendation API</h2></div></div><div class="sc-fQpRED gxopqJ"><div class="sc-euGpHm sc-exayXG fwfkcU kqJXdD redoc-markdown " html="&lt;p&gt;Sophrosyne&amp;#39;s API&lt;/p&gt;
"><p>Sophrosyne&#39;s API</p>
</div></div></div><div id="tag/Recommendation-API/operation/triggerActionRecommendationById" data-section-id="tag/Recommendation-API/operation/triggerActionRecommendationById" class="sc-dsLQwm kcRA-dj"><div data-section-id="operation/triggerActionRecommendationById" id="operation/triggerActionRecommendationById" class="sc-la-DxNn dSIRVR"><div class="sc-fQpRED htdgPt"><h2 class="sc-knesRu cbpGTP"><a class="sc-jCbFiK hSvuOo" href="#tag/Recommendation-API/operation/triggerActionRecommendationById" aria-label="tag/Recommendation-API/operation/triggerActionRecommendationById"></a>Trigger an action recommendation by id<!-- --> </h2><div class="sc-fpJhiv cQxXyG"><div html="&lt;p&gt;Use this endpoint to trigger a Action Recommendation&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD"><p>Use this endpoint to trigger a Action Recommendation</p>
</div></div><div><h5 class="sc-dkjaqt gwrByh">path<!-- --> Parameters</h5><table class="sc-dENhDJ ceVHDP"><tbody><tr class=""><td kind="field" title="id" class="sc-tOkKi sc-epPVmt gbdrVc bUksBx"><span class="sc-hfvVTD hTjFRU"></span><span class="property-name">id</span><div class="sc-xuUkR sc-hrDJJk bJcEcT gLEAmN">required</div></td><td class="sc-fpSrms exGrJC"><div><div><span class="sc-xuUkR sc-cvzDha bJcEcT kDPMlG"></span><span class="sc-xuUkR sc-gKROGD bJcEcT etUsjc">string</span></div> <div><div html="&lt;p&gt;Pass the Action Recommendation&amp;#39;s ID&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"><p>Pass the Action Recommendation&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-tOkKi sc-epPVmt gbdrVc bUksBx"><span class="sc-hfvVTD hTjFRU"></span><span class="property-name">apikey</span><div class="sc-xuUkR sc-hrDJJk bJcEcT gLEAmN">required</div></td><td class="sc-fpSrms exGrJC"><div><div><span class="sc-xuUkR sc-cvzDha bJcEcT kDPMlG"></span><span class="sc-xuUkR sc-gKROGD bJcEcT etUsjc">string</span></div> <div><div html="&lt;p&gt;Pass the Action Recommendation&amp;#39;s Apikey&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"><p>Pass the Action Recommendation&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-eiLgtK dbBFCU">Responses</h3><div><button class="sc-giOWAb dSgpsc" disabled=""><strong class="sc-catHVh gXPvFO">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>successful operation</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">400<!-- --> </strong><div html="&lt;p&gt;Invalid ID supplied&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Invalid ID supplied</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Unauthorized</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">404<!-- --> </strong><div html="&lt;p&gt;Action Recommendation not found&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Action Recommendation not found</p>
</div></button></div></div></div><div class="sc-iKTcqh sc-gnpbhQ fTxZsC drGLlX"><div class="sc-dKsqdn dCbPd"><button class="sc-iAlELC gsBSOU"><span type="post" class="sc-oeqTF kpMtuJ http-verb post">post</span><span class="sc-eowDPD jcAXWA">/api/v1/actionrecommendation/{id}/apikey/{apikey}</span><svg class="sc-cBYhjr iMxoRf" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-ezTrPE bFiOkX"><div class="sc-drnuxz hdRKqQ"><div html="" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"></div><div tabindex="0" role="button"><div class="sc-hDcvty jpmGrk"><span></span>/api/v1/actionrecommendation/{id}/apikey/{apikey}</div></div></div></div></div></div></div></div><div id="tag/Recommendation-API/operation/stopActionRecommendationById" data-section-id="tag/Recommendation-API/operation/stopActionRecommendationById" class="sc-dsLQwm kcRA-dj"><div data-section-id="operation/stopActionRecommendationById" id="operation/stopActionRecommendationById" class="sc-la-DxNn dSIRVR"><div class="sc-fQpRED htdgPt"><h2 class="sc-knesRu cbpGTP"><a class="sc-jCbFiK hSvuOo" href="#tag/Recommendation-API/operation/stopActionRecommendationById" aria-label="tag/Recommendation-API/operation/stopActionRecommendationById"></a>Trigger an action recommendation by id<!-- --> </h2><div class="sc-fpJhiv cQxXyG"><div html="&lt;p&gt;Use this endpoint to trigger a Action Recommendation&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD"><p>Use this endpoint to trigger a Action Recommendation</p>
</div></div><div><h5 class="sc-dkjaqt gwrByh">path<!-- --> Parameters</h5><table class="sc-dENhDJ ceVHDP"><tbody><tr class=""><td kind="field" title="id" class="sc-tOkKi sc-epPVmt gbdrVc bUksBx"><span class="sc-hfvVTD hTjFRU"></span><span class="property-name">id</span><div class="sc-xuUkR sc-hrDJJk bJcEcT gLEAmN">required</div></td><td class="sc-fpSrms exGrJC"><div><div><span class="sc-xuUkR sc-cvzDha bJcEcT kDPMlG"></span><span class="sc-xuUkR sc-gKROGD bJcEcT etUsjc">string</span></div> <div><div html="&lt;p&gt;Pass the Action Recommendation&amp;#39;s ID&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"><p>Pass the Action Recommendation&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-tOkKi sc-epPVmt gbdrVc bUksBx"><span class="sc-hfvVTD hTjFRU"></span><span class="property-name">apikey</span><div class="sc-xuUkR sc-hrDJJk bJcEcT gLEAmN">required</div></td><td class="sc-fpSrms exGrJC"><div><div><span class="sc-xuUkR sc-cvzDha bJcEcT kDPMlG"></span><span class="sc-xuUkR sc-gKROGD bJcEcT etUsjc">string</span></div> <div><div html="&lt;p&gt;Pass the Action Recommendation&amp;#39;s Apikey&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"><p>Pass the Action Recommendation&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-eiLgtK dbBFCU">Responses</h3><div><button class="sc-giOWAb dSgpsc" disabled=""><strong class="sc-catHVh gXPvFO">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>successful operation</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">400<!-- --> </strong><div html="&lt;p&gt;Invalid ID supplied&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Invalid ID supplied</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Unauthorized</p>
</div></button></div><div><button class="sc-giOWAb bEasFS" disabled=""><strong class="sc-catHVh gXPvFO">404<!-- --> </strong><div html="&lt;p&gt;Action Recommendation not found&lt;/p&gt;
" class="sc-euGpHm sc-exayXG fwfkcU kqJXdD sc-dHrNzZ dRdjww"><p>Action Recommendation not found</p>
</div></button></div></div></div><div class="sc-iKTcqh sc-gnpbhQ fTxZsC drGLlX"><div class="sc-dKsqdn dCbPd"><button class="sc-iAlELC gsBSOU"><span type="post" class="sc-oeqTF kpMtuJ http-verb post">post</span><span class="sc-eowDPD jcAXWA">/api/v1/actionrecommendation/{id}/apikey/{apikey}/stop</span><svg class="sc-cBYhjr iMxoRf" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-ezTrPE bFiOkX"><div class="sc-drnuxz hdRKqQ"><div html="" class="sc-euGpHm sc-exayXG fwfkcU jYGAQp"></div><div tabindex="0" role="button"><div class="sc-hDcvty jpmGrk"><span></span>/api/v1/actionrecommendation/{id}/apikey/{apikey}/stop</div></div></div></div></div></div></div></div></div><div class="sc-epzHnm bWkBKa"></div></div></div>
      <script>
      const __redoc_state = {"menu":{"activeItemIdx":-1},"spec":{"data":{"openapi":"3.0.3","info":{"title":"Sophrosyne - Recommendation Service API","description":"This API document describes the available Sophrosyne Recommendation APIs:\n\n1. Trigger a Action Recommendation \n\nCore component of all API - Requests is the Action Recommendation's ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.","version":"1.0.0"},"externalDocs":{"description":"Sophrosyne docs"},"tags":[{"name":"Recommendation API","description":"Sophrosyne's API"}],"paths":{"/api/v1/actionrecommendation/{id}/apikey/{apikey}":{"post":{"tags":["Recommendation API"],"summary":"Trigger an action recommendation by id","description":"Use this endpoint to trigger a Action Recommendation","operationId":"triggerActionRecommendationById","parameters":[{"name":"id","in":"path","description":"Pass the Action Recommendation's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action Recommendation's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid ID supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Action Recommendation not found"}}}},"/api/v1/actionrecommendation/{id}/apikey/{apikey}/stop":{"post":{"tags":["Recommendation API"],"summary":"Trigger an action recommendation by id","description":"Use this endpoint to trigger a Action Recommendation","operationId":"stopActionRecommendationById","parameters":[{"name":"id","in":"path","description":"Pass the Action Recommendation's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action Recommendation's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid ID supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Action Recommendation not found"}}}}},"components":{}}},"searchIndex":{"store":["tag/Recommendation-API","tag/Recommendation-API/operation/triggerActionRecommendationById","tag/Recommendation-API/operation/stopActionRecommendationById"],"index":{"version":"2.3.9","fields":["title","description"],"fieldVectors":[["title/0",[0,0.288,1,0.562]],["description/0",[1,0.613,2,1.28]],["title/1",[0,0.223,3,0.097,4,0.097,5,0.434]],["description/1",[0,0.216,3,0.094,4,0.094,6,0.421,7,0.421,8,0.878]],["title/2",[0,0.223,3,0.097,4,0.097,5,0.434]],["description/2",[0,0.216,3,0.094,4,0.094,6,0.421,7,0.421,9,0.878]]],"invertedIndex":[["action",{"_index":4,"title":{"1":{},"2":{}},"description":{"1":{},"2":{}}}],["api",{"_index":1,"title":{"0":{}},"description":{"0":{}}}],["api/v1/actionrecommendation/{id}/apikey/{apikey",{"_index":8,"title":{},"description":{"1":{}}}],["api/v1/actionrecommendation/{id}/apikey/{apikey}/stop",{"_index":9,"title":{},"description":{"2":{}}}],["endpoint",{"_index":7,"title":{},"description":{"1":{},"2":{}}}],["id",{"_index":5,"title":{"1":{},"2":{}},"description":{}}],["recommend",{"_index":0,"title":{"0":{},"1":{},"2":{}},"description":{"1":{},"2":{}}}],["sophrosyne'",{"_index":2,"title":{},"description":{"0":{}}}],["trigger",{"_index":3,"title":{"1":{},"2":{}},"description":{"1":{},"2":{}}}],["us",{"_index":6,"title":{},"description":{"1":{},"2":{}}}]],"pipeline":[]}},"options":{}};

      var container = document.getElementById('redoc');
      Redoc.hydrate(__redoc_state, container);

      </script>
</body>

</html>