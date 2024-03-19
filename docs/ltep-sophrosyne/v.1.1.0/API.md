# Getting Started - API

Get started with the Sophrosyne API and let your Alerts self-manage.

## API Example - (simple) Action

1. Get your Action ID from the Action Menu
2. Get an allowed Apikey from the Apikey Menu

your-domain:17609/ext/action/6804b76f-224a-433e-840a-5c2f6f4a9a44/apikey/eyJhbGciOiJFUzI1NiJ9

## API Example - Dynamic Action

1. Get your Dynamic Action ID from the Dynamic Action Menu
2. Get an allowed Apikey from the Apikey Menu

your-domain:17609/ext/dynamicaction/b224acdfc-6554a-654e-999a-6804b76f456/apikey/eyJhbGciOiJFUzI1NiJ9

and pass parameters in the JSON-Body
{
    "execution_times": 5,
    "address": "127.0.0.1"
}

<b>OR</b>

pass parameters in the URL-path

your-domain:17609/ext/dynamicaction/b224acdfc-6554a-654e-999a-6804b76f456/parameters/execution_times:5,address:127.0.0.1/apikey/eyJhbGciOiJFUzI1NiJ9

## API Specification

<!DOCTYPE html>
<html>

<head>
  <meta charset="utf8" />
  <title>LTEP Sophrosyne - Service API</title>
  <!-- needed for adaptive design -->
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    body {
      padding: 0;
      margin: 0;
    }
  </style>
  <script src="https://cdn.redoc.ly/redoc/v2.1.3/bundles/redoc.standalone.js"></script><style data-styled="true" data-styled-version="6.1.8">.gikxZY{width:calc(100% - 40%);padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.gikxZY{width:100%;padding:40px 40px;}}/*!sc*/
.jSgyLg{width:calc(100% - 40%);padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.jSgyLg{width:100%;padding:0px 40px;}}/*!sc*/
data-styled.g4[id="sc-hLQSwg"]{content:"gikxZY,jSgyLg,"}/*!sc*/
.hNzKJC{padding:40px 0;}/*!sc*/
.hNzKJC:last-child{min-height:calc(100vh + 1px);}/*!sc*/
.hNzKJC>.hNzKJC:last-child{min-height:initial;}/*!sc*/
@media print,screen and (max-width: 75rem){.hNzKJC{padding:0;}}/*!sc*/
.cSNAXN{padding:40px 0;position:relative;}/*!sc*/
.cSNAXN:last-child{min-height:calc(100vh + 1px);}/*!sc*/
.cSNAXN>.cSNAXN:last-child{min-height:initial;}/*!sc*/
@media print,screen and (max-width: 75rem){.cSNAXN{padding:0;}}/*!sc*/
.cSNAXN:not(:last-of-type):after{position:absolute;bottom:0;width:100%;display:block;content:'';border-bottom:1px solid rgba(0, 0, 0, 0.2);}/*!sc*/
data-styled.g5[id="sc-eDLKkx"]{content:"hNzKJC,cSNAXN,"}/*!sc*/
.imiXRU{width:40%;color:#ffffff;background-color:#263238;padding:0 40px;}/*!sc*/
@media print,screen and (max-width: 75rem){.imiXRU{width:100%;padding:40px 40px;}}/*!sc*/
data-styled.g6[id="sc-jTQCzO"]{content:"imiXRU,"}/*!sc*/
.jGdkPR{background-color:#263238;}/*!sc*/
data-styled.g7[id="sc-gLLuof"]{content:"jGdkPR,"}/*!sc*/
.fsPUig{display:flex;width:100%;padding:0;}/*!sc*/
@media print,screen and (max-width: 75rem){.fsPUig{flex-direction:column;}}/*!sc*/
data-styled.g8[id="sc-iBdnpw"]{content:"fsPUig,"}/*!sc*/
.gqLiaw{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#333333;}/*!sc*/
data-styled.g9[id="sc-fsYfdN"]{content:"gqLiaw,"}/*!sc*/
.gwJLUj{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;margin:0 0 20px;}/*!sc*/
data-styled.g10[id="sc-qZrbh"]{content:"gwJLUj,"}/*!sc*/
.klfnyk{color:#ffffff;}/*!sc*/
data-styled.g12[id="sc-kFCroH"]{content:"klfnyk,"}/*!sc*/
.cnGhhy{border-bottom:1px solid rgba(38, 50, 56, 0.3);margin:1em 0 1em 0;color:rgba(38, 50, 56, 0.5);font-weight:normal;text-transform:uppercase;font-size:0.929em;line-height:20px;}/*!sc*/
data-styled.g13[id="sc-irLvIq"]{content:"cnGhhy,"}/*!sc*/
.fNhImz{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.fNhImz:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
h1:hover>.fNhImz::before,h2:hover>.fNhImz::before,.fNhImz:hover::before{visibility:visible;}/*!sc*/
data-styled.g14[id="sc-csKJxZ"]{content:"fNhImz,"}/*!sc*/
.gEokXu{height:18px;width:18px;min-width:18px;vertical-align:middle;float:right;transition:transform 0.2s ease-out;transform:rotateZ(-90deg);}/*!sc*/
.exoGJA{height:20px;width:20px;min-width:20px;vertical-align:middle;float:right;transition:transform 0.2s ease-out;transform:rotateZ(0);}/*!sc*/
.exoGJA polygon{fill:white;}/*!sc*/
data-styled.g15[id="sc-eTNRI"]{content:"gEokXu,exoGJA,"}/*!sc*/
.cqoAxn{border-left:1px solid #7c7cbb;box-sizing:border-box;position:relative;padding:10px 10px 10px 0;}/*!sc*/
@media screen and (max-width: 50rem){.cqoAxn{display:block;overflow:hidden;}}/*!sc*/
tr:first-of-type>.cqoAxn,tr.last>.cqoAxn{border-left-width:0;background-position:top left;background-repeat:no-repeat;background-size:1px 100%;}/*!sc*/
tr:first-of-type>.cqoAxn{background-image:linear-gradient(
      to bottom,
      transparent 0%,
      transparent 22px,
      #7c7cbb 22px,
      #7c7cbb 100%
    );}/*!sc*/
tr.last>.cqoAxn{background-image:linear-gradient(
      to bottom,
      #7c7cbb 0%,
      #7c7cbb 22px,
      transparent 22px,
      transparent 100%
    );}/*!sc*/
tr.last+tr>.cqoAxn{border-left-color:transparent;}/*!sc*/
tr.last:first-child>.cqoAxn{background:none;border-left-color:transparent;}/*!sc*/
data-styled.g18[id="sc-hABBmJ"]{content:"cqoAxn,"}/*!sc*/
.hfWKVF{vertical-align:top;line-height:20px;white-space:nowrap;font-size:13px;font-family:Courier,monospace;}/*!sc*/
.hfWKVF.deprecated{text-decoration:line-through;color:#707070;}/*!sc*/
data-styled.g20[id="sc-fHejqy"]{content:"hfWKVF,"}/*!sc*/
.berbbf{border-bottom:1px solid #9fb4be;padding:10px 0;width:75%;box-sizing:border-box;}/*!sc*/
tr.expanded .berbbf{border-bottom:none;}/*!sc*/
@media screen and (max-width: 50rem){.berbbf{padding:0 20px;border-bottom:none;border-left:1px solid #7c7cbb;}tr.last>.berbbf{border-left:none;}}/*!sc*/
data-styled.g21[id="sc-blmEgr"]{content:"berbbf,"}/*!sc*/
.hIHfpT{color:#7c7cbb;font-family:Courier,monospace;margin-right:10px;}/*!sc*/
.hIHfpT::before{content:'';display:inline-block;vertical-align:middle;width:10px;height:1px;background:#7c7cbb;}/*!sc*/
.hIHfpT::after{content:'';display:inline-block;vertical-align:middle;width:1px;background:#7c7cbb;height:7px;}/*!sc*/
data-styled.g22[id="sc-ifyrAs"]{content:"hIHfpT,"}/*!sc*/
.kHkWhD{border-collapse:separate;border-radius:3px;font-size:14px;border-spacing:0;width:100%;}/*!sc*/
.kHkWhD >tr{vertical-align:middle;}/*!sc*/
@media screen and (max-width: 50rem){.kHkWhD{display:block;}.kHkWhD >tr,.kHkWhD >tbody>tr{display:block;}}/*!sc*/
@media screen and (max-width: 50rem) and (-ms-high-contrast:none){.kHkWhD td{float:left;width:100%;}}/*!sc*/
.kHkWhD .sc-dJGMql,.kHkWhD .sc-dJGMql .sc-dJGMql .sc-dJGMql,.kHkWhD .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql{margin:1em;margin-right:0;background:#fafafa;}/*!sc*/
.kHkWhD .sc-dJGMql .sc-dJGMql,.kHkWhD .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql,.kHkWhD .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql .sc-dJGMql{background:#ffffff;}/*!sc*/
data-styled.g24[id="sc-hIPBNq"]{content:"kHkWhD,"}/*!sc*/
.jSWvqu >ul{list-style:none;padding:0;margin:0;margin:0 -5px;}/*!sc*/
.jSWvqu >ul >li{padding:5px 10px;display:inline-block;background-color:#11171a;border-bottom:1px solid rgba(0, 0, 0, 0.5);cursor:pointer;text-align:center;outline:none;color:#ccc;margin:0 5px 5px 5px;border:1px solid #07090b;border-radius:5px;min-width:60px;font-size:0.9em;font-weight:bold;}/*!sc*/
.jSWvqu >ul >li.react-tabs__tab--selected{color:#333333;background:#ffffff;}/*!sc*/
.jSWvqu >ul >li.react-tabs__tab--selected:focus{outline:auto;}/*!sc*/
.jSWvqu >ul >li:only-child{flex:none;min-width:100px;}/*!sc*/
.jSWvqu >ul >li.tab-success{color:#1d8127;}/*!sc*/
.jSWvqu >ul >li.tab-redirect{color:#ffa500;}/*!sc*/
.jSWvqu >ul >li.tab-info{color:#87ceeb;}/*!sc*/
.jSWvqu >ul >li.tab-error{color:#d41f1c;}/*!sc*/
.jSWvqu >.react-tabs__tab-panel{background:#11171a;}/*!sc*/
.jSWvqu >.react-tabs__tab-panel>div,.jSWvqu >.react-tabs__tab-panel>pre{padding:20px;margin:0;}/*!sc*/
.jSWvqu >.react-tabs__tab-panel>div>pre{padding:0;}/*!sc*/
data-styled.g30[id="sc-cyZbeP"]{content:"jSWvqu,"}/*!sc*/
.WVNwY code[class*='language-'],.WVNwY pre[class*='language-']{text-shadow:0 -0.1em 0.2em black;text-align:left;white-space:pre;word-spacing:normal;word-break:normal;word-wrap:normal;line-height:1.5;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;}/*!sc*/
@media print{.WVNwY code[class*='language-'],.WVNwY pre[class*='language-']{text-shadow:none;}}/*!sc*/
.WVNwY pre[class*='language-']{padding:1em;margin:0.5em 0;overflow:auto;}/*!sc*/
.WVNwY .token.comment,.WVNwY .token.prolog,.WVNwY .token.doctype,.WVNwY .token.cdata{color:hsl(30, 20%, 50%);}/*!sc*/
.WVNwY .token.punctuation{opacity:0.7;}/*!sc*/
.WVNwY .namespace{opacity:0.7;}/*!sc*/
.WVNwY .token.property,.WVNwY .token.tag,.WVNwY .token.number,.WVNwY .token.constant,.WVNwY .token.symbol{color:#4a8bb3;}/*!sc*/
.WVNwY .token.boolean{color:#e64441;}/*!sc*/
.WVNwY .token.selector,.WVNwY .token.attr-name,.WVNwY .token.string,.WVNwY .token.char,.WVNwY .token.builtin,.WVNwY .token.inserted{color:#a0fbaa;}/*!sc*/
.WVNwY .token.selector+a,.WVNwY .token.attr-name+a,.WVNwY .token.string+a,.WVNwY .token.char+a,.WVNwY .token.builtin+a,.WVNwY .token.inserted+a,.WVNwY .token.selector+a:visited,.WVNwY .token.attr-name+a:visited,.WVNwY .token.string+a:visited,.WVNwY .token.char+a:visited,.WVNwY .token.builtin+a:visited,.WVNwY .token.inserted+a:visited{color:#4ed2ba;text-decoration:underline;}/*!sc*/
.WVNwY .token.property.string{color:white;}/*!sc*/
.WVNwY .token.operator,.WVNwY .token.entity,.WVNwY .token.url,.WVNwY .token.variable{color:hsl(40, 90%, 60%);}/*!sc*/
.WVNwY .token.atrule,.WVNwY .token.attr-value,.WVNwY .token.keyword{color:hsl(350, 40%, 70%);}/*!sc*/
.WVNwY .token.regex,.WVNwY .token.important{color:#e90;}/*!sc*/
.WVNwY .token.important,.WVNwY .token.bold{font-weight:bold;}/*!sc*/
.WVNwY .token.italic{font-style:italic;}/*!sc*/
.WVNwY .token.entity{cursor:help;}/*!sc*/
.WVNwY .token.deleted{color:red;}/*!sc*/
data-styled.g32[id="sc-iKOmoZ"]{content:"WVNwY,"}/*!sc*/
.iwAAMv{opacity:0.7;transition:opacity 0.3s ease;text-align:right;}/*!sc*/
.iwAAMv:focus-within{opacity:1;}/*!sc*/
.iwAAMv >button{background-color:transparent;border:0;color:inherit;padding:2px 10px;font-family:Roboto,sans-serif;font-size:14px;line-height:1.5em;cursor:pointer;outline:0;}/*!sc*/
.iwAAMv >button :hover,.iwAAMv >button :focus{background:rgba(255, 255, 255, 0.1);}/*!sc*/
data-styled.g33[id="sc-gjLLEI"]{content:"iwAAMv,"}/*!sc*/
.kIqtpW{position:relative;}/*!sc*/
data-styled.g37[id="sc-kMzELR"]{content:"kIqtpW,"}/*!sc*/
.hJSqDi{margin-left:10px;text-transform:none;font-size:0.929em;color:black;}/*!sc*/
data-styled.g41[id="sc-gYrqIg"]{content:"hJSqDi,"}/*!sc*/
.VEBGS{font-family:Roboto,sans-serif;font-weight:400;line-height:1.5em;}/*!sc*/
.VEBGS p:last-child{margin-bottom:0;}/*!sc*/
.VEBGS h1{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#32329f;margin-top:0;}/*!sc*/
.VEBGS h2{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;}/*!sc*/
.VEBGS code{color:#e53935;background-color:rgba(38, 50, 56, 0.05);font-family:Courier,monospace;border-radius:2px;border:1px solid rgba(38, 50, 56, 0.1);padding:0 5px;font-size:13px;font-weight:400;word-break:break-word;}/*!sc*/
.VEBGS pre{font-family:Courier,monospace;white-space:pre;background-color:#11171a;color:white;padding:20px;overflow-x:auto;line-height:normal;border-radius:0;border:1px solid rgba(38, 50, 56, 0.1);}/*!sc*/
.VEBGS pre code{background-color:transparent;color:white;padding:0;}/*!sc*/
.VEBGS pre code:before,.VEBGS pre code:after{content:none;}/*!sc*/
.VEBGS blockquote{margin:0;margin-bottom:1em;padding:0 15px;color:#777;border-left:4px solid #ddd;}/*!sc*/
.VEBGS img{max-width:100%;box-sizing:content-box;}/*!sc*/
.VEBGS ul,.VEBGS ol{padding-left:2em;margin:0;margin-bottom:1em;}/*!sc*/
.VEBGS ul ul,.VEBGS ol ul,.VEBGS ul ol,.VEBGS ol ol{margin-bottom:0;margin-top:0;}/*!sc*/
.VEBGS table{display:block;width:100%;overflow:auto;word-break:normal;word-break:keep-all;border-collapse:collapse;border-spacing:0;margin-top:1.5em;margin-bottom:1.5em;}/*!sc*/
.VEBGS table tr{background-color:#fff;border-top:1px solid #ccc;}/*!sc*/
.VEBGS table tr:nth-child(2n){background-color:#fafafa;}/*!sc*/
.VEBGS table th,.VEBGS table td{padding:6px 13px;border:1px solid #ddd;}/*!sc*/
.VEBGS table th{text-align:left;font-weight:bold;}/*!sc*/
.VEBGS .share-link{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.VEBGS .share-link:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
.VEBGS h1:hover>.share-link::before,.VEBGS h2:hover>.share-link::before,.VEBGS .share-link:hover::before{visibility:visible;}/*!sc*/
.VEBGS a{text-decoration:auto;color:#32329f;}/*!sc*/
.VEBGS a:visited{color:#32329f;}/*!sc*/
.VEBGS a:hover{color:#6868cf;text-decoration:auto;}/*!sc*/
.jaVotg{font-family:Roboto,sans-serif;font-weight:400;line-height:1.5em;}/*!sc*/
.jaVotg p:last-child{margin-bottom:0;}/*!sc*/
.jaVotg p:first-child{margin-top:0;}/*!sc*/
.jaVotg p:last-child{margin-bottom:0;}/*!sc*/
.jaVotg h1{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.85714em;line-height:1.6em;color:#32329f;margin-top:0;}/*!sc*/
.jaVotg h2{font-family:Montserrat,sans-serif;font-weight:400;font-size:1.57143em;line-height:1.6em;color:#333333;}/*!sc*/
.jaVotg code{color:#e53935;background-color:rgba(38, 50, 56, 0.05);font-family:Courier,monospace;border-radius:2px;border:1px solid rgba(38, 50, 56, 0.1);padding:0 5px;font-size:13px;font-weight:400;word-break:break-word;}/*!sc*/
.jaVotg pre{font-family:Courier,monospace;white-space:pre;background-color:#11171a;color:white;padding:20px;overflow-x:auto;line-height:normal;border-radius:0;border:1px solid rgba(38, 50, 56, 0.1);}/*!sc*/
.jaVotg pre code{background-color:transparent;color:white;padding:0;}/*!sc*/
.jaVotg pre code:before,.jaVotg pre code:after{content:none;}/*!sc*/
.jaVotg blockquote{margin:0;margin-bottom:1em;padding:0 15px;color:#777;border-left:4px solid #ddd;}/*!sc*/
.jaVotg img{max-width:100%;box-sizing:content-box;}/*!sc*/
.jaVotg ul,.jaVotg ol{padding-left:2em;margin:0;margin-bottom:1em;}/*!sc*/
.jaVotg ul ul,.jaVotg ol ul,.jaVotg ul ol,.jaVotg ol ol{margin-bottom:0;margin-top:0;}/*!sc*/
.jaVotg table{display:block;width:100%;overflow:auto;word-break:normal;word-break:keep-all;border-collapse:collapse;border-spacing:0;margin-top:1.5em;margin-bottom:1.5em;}/*!sc*/
.jaVotg table tr{background-color:#fff;border-top:1px solid #ccc;}/*!sc*/
.jaVotg table tr:nth-child(2n){background-color:#fafafa;}/*!sc*/
.jaVotg table th,.jaVotg table td{padding:6px 13px;border:1px solid #ddd;}/*!sc*/
.jaVotg table th{text-align:left;font-weight:bold;}/*!sc*/
.jaVotg .share-link{cursor:pointer;margin-left:-20px;padding:0;line-height:1;width:20px;display:inline-block;outline:0;}/*!sc*/
.jaVotg .share-link:before{content:'';width:15px;height:15px;background-size:contain;background-image:url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgeD0iMCIgeT0iMCIgd2lkdGg9IjUxMiIgaGVpZ2h0PSI1MTIiIHZpZXdCb3g9IjAgMCA1MTIgNTEyIiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCA1MTIgNTEyIiB4bWw6c3BhY2U9InByZXNlcnZlIj48cGF0aCBmaWxsPSIjMDEwMTAxIiBkPSJNNDU5LjcgMjMzLjRsLTkwLjUgOTAuNWMtNTAgNTAtMTMxIDUwLTE4MSAwIC03LjktNy44LTE0LTE2LjctMTkuNC0yNS44bDQyLjEtNDIuMWMyLTIgNC41LTMuMiA2LjgtNC41IDIuOSA5LjkgOCAxOS4zIDE1LjggMjcuMiAyNSAyNSA2NS42IDI0LjkgOTAuNSAwbDkwLjUtOTAuNWMyNS0yNSAyNS02NS42IDAtOTAuNSAtMjQuOS0yNS02NS41LTI1LTkwLjUgMGwtMzIuMiAzMi4yYy0yNi4xLTEwLjItNTQuMi0xMi45LTgxLjYtOC45bDY4LjYtNjguNmM1MC01MCAxMzEtNTAgMTgxIDBDNTA5LjYgMTAyLjMgNTA5LjYgMTgzLjQgNDU5LjcgMjMzLjR6TTIyMC4zIDM4Mi4ybC0zMi4yIDMyLjJjLTI1IDI0LjktNjUuNiAyNC45LTkwLjUgMCAtMjUtMjUtMjUtNjUuNiAwLTkwLjVsOTAuNS05MC41YzI1LTI1IDY1LjUtMjUgOTAuNSAwIDcuOCA3LjggMTIuOSAxNy4yIDE1LjggMjcuMSAyLjQtMS40IDQuOC0yLjUgNi44LTQuNWw0Mi4xLTQyYy01LjQtOS4yLTExLjYtMTgtMTkuNC0yNS44IC01MC01MC0xMzEtNTAtMTgxIDBsLTkwLjUgOTAuNWMtNTAgNTAtNTAgMTMxIDAgMTgxIDUwIDUwIDEzMSA1MCAxODEgMGw2OC42LTY4LjZDMjc0LjYgMzk1LjEgMjQ2LjQgMzkyLjMgMjIwLjMgMzgyLjJ6Ii8+PC9zdmc+Cg==');opacity:0.5;visibility:hidden;display:inline-block;vertical-align:middle;}/*!sc*/
.jaVotg h1:hover>.share-link::before,.jaVotg h2:hover>.share-link::before,.jaVotg .share-link:hover::before{visibility:visible;}/*!sc*/
.jaVotg a{text-decoration:auto;color:#32329f;}/*!sc*/
.jaVotg a:visited{color:#32329f;}/*!sc*/
.jaVotg a:hover{color:#6868cf;text-decoration:auto;}/*!sc*/
data-styled.g42[id="sc-cCzLxZ"]{content:"VEBGS,jaVotg,"}/*!sc*/
.LxEPk{display:inline;}/*!sc*/
data-styled.g43[id="sc-ckdEwu"]{content:"LxEPk,"}/*!sc*/
.krcPXE{position:relative;}/*!sc*/
data-styled.g44[id="sc-jdHILj"]{content:"krcPXE,"}/*!sc*/
.fOJBdW:hover>.sc-gjLLEI{opacity:1;}/*!sc*/
data-styled.g49[id="sc-cSxRuM"]{content:"fOJBdW,"}/*!sc*/
.DqFKH{font-family:Courier,monospace;font-size:13px;white-space:pre;contain:content;overflow-x:auto;}/*!sc*/
.DqFKH .redoc-json code>.collapser{display:none;pointer-events:none;}/*!sc*/
.DqFKH .callback-function{color:gray;}/*!sc*/
.DqFKH .collapser:after{content:'-';cursor:pointer;}/*!sc*/
.DqFKH .collapsed>.collapser:after{content:'+';cursor:pointer;}/*!sc*/
.DqFKH .ellipsis:after{content:' … ';}/*!sc*/
.DqFKH .collapsible{margin-left:2em;}/*!sc*/
.DqFKH .hoverable{padding-top:1px;padding-bottom:1px;padding-left:2px;padding-right:2px;border-radius:2px;}/*!sc*/
.DqFKH .hovered{background-color:rgba(235, 238, 249, 1);}/*!sc*/
.DqFKH .collapser{background-color:transparent;border:0;color:#fff;font-family:Courier,monospace;font-size:13px;padding-right:6px;padding-left:6px;padding-top:0;padding-bottom:0;display:flex;align-items:center;justify-content:center;width:15px;height:15px;position:absolute;top:4px;left:-1.5em;cursor:default;user-select:none;-webkit-user-select:none;padding:2px;}/*!sc*/
.DqFKH .collapser:focus{outline-color:#fff;outline-style:dotted;outline-width:1px;}/*!sc*/
.DqFKH ul{list-style-type:none;padding:0px;margin:0px 0px 0px 26px;}/*!sc*/
.DqFKH li{position:relative;display:block;}/*!sc*/
.DqFKH .hoverable{display:inline-block;}/*!sc*/
.DqFKH .selected{outline-style:solid;outline-width:1px;outline-style:dotted;}/*!sc*/
.DqFKH .collapsed>.collapsible{display:none;}/*!sc*/
.DqFKH .ellipsis{display:none;}/*!sc*/
.DqFKH .collapsed>.ellipsis{display:inherit;}/*!sc*/
data-styled.g50[id="sc-jMbVJB"]{content:"DqFKH,"}/*!sc*/
.jCmKdj{padding:0.9em;background-color:rgba(38,50,56,0.4);margin:0 0 10px 0;display:block;font-family:Montserrat,sans-serif;font-size:0.929em;line-height:1.5em;}/*!sc*/
data-styled.g51[id="sc-dQmiwx"]{content:"jCmKdj,"}/*!sc*/
.eTZsJr{font-family:Montserrat,sans-serif;font-size:12px;position:absolute;z-index:1;top:-11px;left:12px;font-weight:600;color:rgba(255,255,255,0.7);}/*!sc*/
data-styled.g52[id="sc-bCvmQg"]{content:"eTZsJr,"}/*!sc*/
.jBjImi{position:relative;}/*!sc*/
data-styled.g53[id="sc-cPtzlb"]{content:"jBjImi,"}/*!sc*/
.jeLSWq{margin-top:15px;}/*!sc*/
data-styled.g56[id="sc-hVcFVo"]{content:"jeLSWq,"}/*!sc*/
.itHPsH{vertical-align:middle;font-size:13px;line-height:20px;}/*!sc*/
data-styled.g58[id="sc-gUjWJS"]{content:"itHPsH,"}/*!sc*/
.iSyacY{color:rgba(102,102,102,0.9);}/*!sc*/
data-styled.g59[id="sc-kZOsHZ"]{content:"iSyacY,"}/*!sc*/
.gfdSsP{color:#666;}/*!sc*/
data-styled.g60[id="sc-iLXxbI"]{content:"gfdSsP,"}/*!sc*/
.ciWJhv{color:#d41f1c;font-size:0.9em;font-weight:normal;margin-left:20px;line-height:1;}/*!sc*/
data-styled.g62[id="sc-eKzvBH"]{content:"ciWJhv,"}/*!sc*/
.cRxwgg{border-radius:2px;word-break:break-word;background-color:rgba(51,51,51,0.05);color:rgba(51,51,51,0.9);padding:0 5px;border:1px solid rgba(51,51,51,0.1);font-family:Courier,monospace;}/*!sc*/
+{margin-left:0;}/*!sc*/
data-styled.g66[id="sc-ldgOGP"]{content:"cRxwgg,"}/*!sc*/
.hgVHfA{margin:1em 0;}/*!sc*/
.hgVHfA a{text-decoration:auto;color:#32329f;}/*!sc*/
.hgVHfA a:visited{color:#32329f;}/*!sc*/
.hgVHfA a:hover{color:#6868cf;text-decoration:auto;}/*!sc*/
data-styled.g70[id="sc-EFWon"]{content:"hgVHfA,"}/*!sc*/
.ObWVe{margin-top:0;margin-bottom:0.5em;}/*!sc*/
data-styled.g91[id="sc-eFyDpN"]{content:"ObWVe,"}/*!sc*/
.iGcmRf{border:1px solid #32329f;color:#32329f;font-weight:normal;margin-left:0.5em;padding:4px 8px 4px;display:inline-block;text-decoration:none;cursor:pointer;}/*!sc*/
data-styled.g92[id="sc-crHHJw"]{content:"iGcmRf,"}/*!sc*/
.bTPOee::before{content:'|';display:inline-block;opacity:0.5;width:15px;text-align:center;}/*!sc*/
.bTPOee:last-child::after{display:none;}/*!sc*/
data-styled.g93[id="sc-dEFUer"]{content:"bTPOee,"}/*!sc*/
.fiaqWn{overflow:hidden;}/*!sc*/
data-styled.g94[id="sc-bqOYya"]{content:"fiaqWn,"}/*!sc*/
.jqfeha{display:flex;flex-wrap:wrap;margin-left:-15px;}/*!sc*/
data-styled.g95[id="sc-gHjVMF"]{content:"jqfeha,"}/*!sc*/
.gxSVta{width:9ex;display:inline-block;height:13px;line-height:13px;background-color:#333;border-radius:3px;background-repeat:no-repeat;background-position:6px 4px;font-size:7px;font-family:Verdana,sans-serif;color:white;text-transform:uppercase;text-align:center;font-weight:bold;vertical-align:middle;margin-right:6px;margin-top:2px;}/*!sc*/
.gxSVta.get{background-color:#2F8132;}/*!sc*/
.gxSVta.post{background-color:#186FAF;}/*!sc*/
.gxSVta.put{background-color:#95507c;}/*!sc*/
.gxSVta.options{background-color:#947014;}/*!sc*/
.gxSVta.patch{background-color:#bf581d;}/*!sc*/
.gxSVta.delete{background-color:#cc3333;}/*!sc*/
.gxSVta.basic{background-color:#707070;}/*!sc*/
.gxSVta.link{background-color:#07818F;}/*!sc*/
.gxSVta.head{background-color:#A23DAD;}/*!sc*/
.gxSVta.hook{background-color:#32329f;}/*!sc*/
.gxSVta.schema{background-color:#707070;}/*!sc*/
data-styled.g99[id="sc-dmcoYd"]{content:"gxSVta,"}/*!sc*/
.fTlmpg{margin:0;padding:0;}/*!sc*/
.fTlmpg:first-child{padding-bottom:32px;}/*!sc*/
.sc-YltrM .sc-YltrM{font-size:0.929em;}/*!sc*/
.dOKzVh{margin:0;padding:0;display:none;}/*!sc*/
.dOKzVh:first-child{padding-bottom:32px;}/*!sc*/
.sc-YltrM .sc-YltrM{font-size:0.929em;}/*!sc*/
data-styled.g100[id="sc-YltrM"]{content:"fTlmpg,dOKzVh,"}/*!sc*/
.kIUuLW{list-style:none inside none;overflow:hidden;text-overflow:ellipsis;padding:0;}/*!sc*/
data-styled.g101[id="sc-imiRDh"]{content:"kIUuLW,"}/*!sc*/
.jtSMDN{cursor:pointer;color:#333333;margin:0;padding:12.5px 20px;display:flex;justify-content:space-between;font-family:Montserrat,sans-serif;font-size:0.929em;text-transform:none;background-color:#fafafa;}/*!sc*/
.jtSMDN:hover{color:#32329f;background-color:#e1e1e1;}/*!sc*/
.jtSMDN .sc-eTNRI{height:1.5em;width:1.5em;}/*!sc*/
.jtSMDN .sc-eTNRI polygon{fill:#333333;}/*!sc*/
.gvinAL{cursor:pointer;color:#333333;margin:0;padding:12.5px 20px;display:flex;justify-content:space-between;font-family:Montserrat,sans-serif;background-color:#fafafa;}/*!sc*/
.gvinAL:hover{color:#32329f;background-color:#ededed;}/*!sc*/
.gvinAL .sc-eTNRI{height:1.5em;width:1.5em;}/*!sc*/
.gvinAL .sc-eTNRI polygon{fill:#333333;}/*!sc*/
data-styled.g102[id="sc-vIyEI"]{content:"jtSMDN,gvinAL,"}/*!sc*/
.fXgHFV{display:inline-block;vertical-align:middle;width:calc(100% - 38px);overflow:hidden;text-overflow:ellipsis;}/*!sc*/
data-styled.g103[id="sc-bjUHJT"]{content:"fXgHFV,"}/*!sc*/
.dWVQcL{font-size:0.8em;margin-top:10px;text-align:center;position:fixed;width:260px;bottom:0;background:#fafafa;}/*!sc*/
.dWVQcL a,.dWVQcL a:visited,.dWVQcL a:hover{color:#333333!important;padding:5px 0;border-top:1px solid #e1e1e1;text-decoration:none;display:flex;align-items:center;justify-content:center;}/*!sc*/
.dWVQcL img{width:15px;margin-right:5px;}/*!sc*/
@media screen and (max-width: 50rem){.dWVQcL{width:100%;}}/*!sc*/
data-styled.g104[id="sc-eIPYkq"]{content:"dWVQcL,"}/*!sc*/
.cIsduN{cursor:pointer;position:relative;margin-bottom:5px;}/*!sc*/
data-styled.g110[id="sc-bPrlCs"]{content:"cIsduN,"}/*!sc*/
.gllLir{font-family:Courier,monospace;margin-left:10px;flex:1;overflow-x:hidden;text-overflow:ellipsis;}/*!sc*/
data-styled.g111[id="sc-fYrVWQ"]{content:"gllLir,"}/*!sc*/
.bclCVA{outline:0;color:inherit;width:100%;text-align:left;cursor:pointer;padding:10px 30px 10px 20px;border-radius:4px 4px 0 0;background-color:#11171a;display:flex;white-space:nowrap;align-items:center;border:1px solid transparent;border-bottom:0;transition:border-color 0.25s ease;}/*!sc*/
.bclCVA ..sc-fYrVWQ{color:#ffffff;}/*!sc*/
.bclCVA:focus{box-shadow:inset 0 2px 2px rgba(0, 0, 0, 0.45),0 2px 0 rgba(128, 128, 128, 0.25);}/*!sc*/
data-styled.g112[id="sc-GkLId"]{content:"bclCVA,"}/*!sc*/
.jBKVIL{font-size:0.929em;line-height:20px;background-color:#186FAF;color:#ffffff;padding:3px 10px;text-transform:uppercase;font-family:Montserrat,sans-serif;margin:0;}/*!sc*/
data-styled.g113[id="sc-jYnQyy"]{content:"jBKVIL,"}/*!sc*/
.hsEiws{position:absolute;width:100%;z-index:100;background:#fafafa;color:#263238;box-sizing:border-box;box-shadow:0 0 6px rgba(0, 0, 0, 0.33);overflow:hidden;border-bottom-left-radius:4px;border-bottom-right-radius:4px;transition:all 0.25s ease;visibility:hidden;transform:translateY(-50%) scaleY(0);}/*!sc*/
data-styled.g114[id="sc-eGgGjL"]{content:"hsEiws,"}/*!sc*/
.jerStl{padding:10px;}/*!sc*/
data-styled.g115[id="sc-fnpiog"]{content:"jerStl,"}/*!sc*/
.etvaCd{padding:5px;border:1px solid #ccc;background:#fff;word-break:break-all;color:#32329f;}/*!sc*/
.etvaCd >span{color:#333333;}/*!sc*/
data-styled.g116[id="sc-lkDHyp"]{content:"etvaCd,"}/*!sc*/
.iSOCsR{display:block;border:0;width:100%;text-align:left;padding:10px;border-radius:2px;margin-bottom:4px;line-height:1.5em;cursor:pointer;color:#1d8127;background-color:rgba(29,129,39,0.07);cursor:default;}/*!sc*/
.iSOCsR:focus{outline:auto #1d8127;}/*!sc*/
.iSOCsR::before{content:"—";font-weight:bold;width:1.5em;text-align:center;display:inline-block;vertical-align:top;}/*!sc*/
.iSOCsR:focus{outline:0;}/*!sc*/
.ifZPCr{display:block;border:0;width:100%;text-align:left;padding:10px;border-radius:2px;margin-bottom:4px;line-height:1.5em;cursor:pointer;color:#d41f1c;background-color:rgba(212,31,28,0.07);cursor:default;}/*!sc*/
.ifZPCr:focus{outline:auto #d41f1c;}/*!sc*/
.ifZPCr::before{content:"—";font-weight:bold;width:1.5em;text-align:center;display:inline-block;vertical-align:top;}/*!sc*/
.ifZPCr:focus{outline:0;}/*!sc*/
data-styled.g119[id="sc-hsaIUA"]{content:"iSOCsR,ifZPCr,"}/*!sc*/
.ePkkgX{vertical-align:top;}/*!sc*/
data-styled.g122[id="sc-gWQvRS"]{content:"ePkkgX,"}/*!sc*/
.duKVDl{font-size:1.3em;padding:0.2em 0;margin:3em 0 1.1em;color:#333333;font-weight:normal;}/*!sc*/
data-styled.g123[id="sc-fYitVF"]{content:"duKVDl,"}/*!sc*/
.dZbpPF{margin-bottom:30px;}/*!sc*/
data-styled.g128[id="sc-eYFTNc"]{content:"dZbpPF,"}/*!sc*/
.bUvUmx{user-select:none;width:20px;height:20px;align-self:center;display:flex;flex-direction:column;color:#32329f;}/*!sc*/
data-styled.g129[id="sc-iEYVpv"]{content:"bUvUmx,"}/*!sc*/
.hHYXMN{width:260px;background-color:#fafafa;overflow:hidden;display:flex;flex-direction:column;backface-visibility:hidden;height:100vh;position:sticky;position:-webkit-sticky;top:0;}/*!sc*/
@media screen and (max-width: 50rem){.hHYXMN{position:fixed;z-index:20;width:100%;background:#fafafa;display:none;}}/*!sc*/
@media print{.hHYXMN{display:none;}}/*!sc*/
data-styled.g130[id="sc-iqziPC"]{content:"hHYXMN,"}/*!sc*/
.kHszPm{outline:none;user-select:none;background-color:#f2f2f2;color:#32329f;display:none;cursor:pointer;position:fixed;right:20px;z-index:100;border-radius:50%;box-shadow:0 0 20px rgba(0, 0, 0, 0.3);bottom:44px;width:60px;height:60px;padding:0 20px;}/*!sc*/
@media screen and (max-width: 50rem){.kHszPm{display:flex;}}/*!sc*/
.kHszPm svg{color:#0065FB;}/*!sc*/
@media print{.kHszPm{display:none;}}/*!sc*/
data-styled.g131[id="sc-eXzmLu"]{content:"kHszPm,"}/*!sc*/
.cSYMrW{font-family:Roboto,sans-serif;font-size:14px;font-weight:400;line-height:1.5em;color:#333333;display:flex;position:relative;text-align:left;-webkit-font-smoothing:antialiased;font-smoothing:antialiased;text-rendering:optimizeSpeed!important;tap-highlight-color:rgba(0, 0, 0, 0);text-size-adjust:100%;}/*!sc*/
.cSYMrW *{box-sizing:border-box;-webkit-tap-highlight-color:rgba(255, 255, 255, 0);}/*!sc*/
data-styled.g132[id="sc-kUNLVD"]{content:"cSYMrW,"}/*!sc*/
.cOuMek{z-index:1;position:relative;overflow:hidden;width:calc(100% - 260px);contain:layout;}/*!sc*/
@media print,screen and (max-width: 50rem){.cOuMek{width:100%;}}/*!sc*/
data-styled.g133[id="sc-dxfTlo"]{content:"cOuMek,"}/*!sc*/
.bsunyy{background:#263238;position:absolute;top:0;bottom:0;right:0;width:calc((100% - 260px) * 0.4);}/*!sc*/
@media print,screen and (max-width: 75rem){.bsunyy{display:none;}}/*!sc*/
data-styled.g134[id="sc-juusvx"]{content:"bsunyy,"}/*!sc*/
.cUtpgV{padding:5px 0;}/*!sc*/
data-styled.g135[id="sc-emwzcK"]{content:"cUtpgV,"}/*!sc*/
.iiRHzu{width:calc(100% - 40px);box-sizing:border-box;margin:0 20px;padding:5px 10px 5px 20px;border:0;border-bottom:1px solid #e1e1e1;font-family:Roboto,sans-serif;font-weight:bold;font-size:13px;color:#333333;background-color:transparent;outline:none;}/*!sc*/
data-styled.g136[id="sc-kjKYmT"]{content:"iiRHzu,"}/*!sc*/
.dvQijr{position:absolute;left:20px;height:1.8em;width:0.9em;}/*!sc*/
.dvQijr path{fill:#333333;}/*!sc*/
data-styled.g137[id="sc-cMdfCE"]{content:"dvQijr,"}/*!sc*/
</style>
  <link href="https://fonts.googleapis.com/css?family=Montserrat:300,400,700|Roboto:300,400,700" rel="stylesheet">
</head>

<body>
  
      <div id="redoc"><div class="sc-kUNLVD cSYMrW redoc-wrap"><div class="sc-iqziPC hHYXMN menu-content" style="top:0px;height:calc(100vh - 0px)"><div role="search" class="sc-emwzcK cUtpgV"><svg class="sc-cMdfCE dvQijr search-icon" version="1.1" viewBox="0 0 1000 1000" x="0px" xmlns="http://www.w3.org/2000/svg" y="0px"><path d="M968.2,849.4L667.3,549c83.9-136.5,66.7-317.4-51.7-435.6C477.1-25,252.5-25,113.9,113.4c-138.5,138.3-138.5,362.6,0,501C219.2,730.1,413.2,743,547.6,666.5l301.9,301.4c43.6,43.6,76.9,14.9,104.2-12.4C981,928.3,1011.8,893,968.2,849.4z M524.5,522c-88.9,88.7-233,88.7-321.8,0c-88.9-88.7-88.9-232.6,0-321.3c88.9-88.7,233-88.7,321.8,0C613.4,289.4,613.4,433.3,524.5,522z"></path></svg><input placeholder="Search..." aria-label="Search" type="text" class="sc-kjKYmT iiRHzu search-input" value=""/></div><div class="sc-kMzELR kIqtpW scrollbar-container undefined"><ul role="menu" class="sc-YltrM fTlmpg"><li tabindex="0" depth="1" data-item-id="tag/API" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI jtSMDN -depth1"><span width="calc(100% - 38px)" title="API" class="sc-bjUHJT fXgHFV">API</span><svg class="sc-eTNRI gEokXu" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></label><ul class="sc-YltrM dOKzVh"><li tabindex="0" depth="2" data-item-id="tag/API/operation/executeAction" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI gvinAL -depth2"><span type="post" class="sc-dmcoYd gxSVta operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-bjUHJT fXgHFV">Execute action by id</span></label></li><li tabindex="0" depth="2" data-item-id="tag/API/operation/executeDynamicAction" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI gvinAL -depth2"><span type="post" class="sc-dmcoYd gxSVta operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-bjUHJT fXgHFV">Execute dynamic action by id</span></label></li><li tabindex="0" depth="2" data-item-id="tag/API/operation/executeDynamicActionParamsInBody" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI gvinAL -depth2"><span type="post" class="sc-dmcoYd gxSVta operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-bjUHJT fXgHFV">Execute dynamic action by id</span></label></li><li tabindex="0" depth="2" data-item-id="tag/API/operation/stopAction" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI gvinAL -depth2"><span type="post" class="sc-dmcoYd gxSVta operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-bjUHJT fXgHFV">Stop action execution by id</span></label></li><li tabindex="0" depth="2" data-item-id="tag/API/operation/stopDynamicAction" role="menuitem" class="sc-imiRDh kIUuLW"><label class="sc-vIyEI gvinAL -depth2"><span type="post" class="sc-dmcoYd gxSVta operation-type post">post</span><span tabindex="0" width="calc(100% - 38px)" class="sc-bjUHJT fXgHFV">Stop dynamic action execution by id</span></label></li></ul></li></ul><div class="sc-eIPYkq dWVQcL"><a target="_blank" rel="noopener noreferrer" href="https://redocly.com/redoc/">API docs by Redocly</a></div></div></div><div class="sc-eXzmLu kHszPm"><div class="sc-iEYVpv bUvUmx"><svg class="" style="transform:translate(2px, -4px) rotate(180deg);transition:transform 0.2s ease" viewBox="0 0 926.23699 573.74994" version="1.1" x="0px" y="0px" width="15" height="15"><g transform="translate(904.92214,-879.1482)"><path d="
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
        " fill="currentColor"></path></g></svg></div></div><div class="sc-dxfTlo cOuMek api-content"><div class="sc-eDLKkx hNzKJC"><div class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY api-info"><h1 class="sc-fsYfdN sc-eFyDpN gqLiaw ObWVe">LTEP Sophrosyne - Service API<!-- --> <span>(<!-- -->1.1.0<!-- -->)</span></h1><p>Download OpenAPI specification<!-- -->:<a download="openapi.json" target="_blank" class="sc-crHHJw iGcmRf">Download</a></p><div class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><div class="sc-bqOYya fiaqWn"><div class="sc-gHjVMF jqfeha"><span class="sc-dEFUer bTPOee">E-mail<!-- -->:<!-- --> <a href="mailto:efstratios.pahis@ltep-technologies.com">efstratios.pahis@ltep-technologies.com</a></span> <!-- --> <span class="sc-dEFUer bTPOee">License:<!-- --> <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a></span> </div></div></div><div data-role="redoc-summary" html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"></div><div data-role="redoc-description" html="&lt;p&gt;This API document describes the available LTEP Sophrosyne Action APIs.&lt;/p&gt;
&lt;ol&gt;
&lt;li&gt;Trigger a simple Action without passing any parameters&lt;/li&gt;
&lt;li&gt;Trigger a Dynamic Action passing parameters in the path using interpolation&lt;/li&gt;
&lt;li&gt;Trigger a Dynamic Action passing parameters in the body as JSON&lt;/li&gt;
&lt;/ol&gt;
&lt;p&gt;Core component of all API - Requests is the Action&amp;#39;s ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>This API document describes the available LTEP Sophrosyne Action APIs.</p>
<ol>
<li>Trigger a simple Action without passing any parameters</li>
<li>Trigger a Dynamic Action passing parameters in the path using interpolation</li>
<li>Trigger a Dynamic Action passing parameters in the body as JSON</li>
</ol>
<p>Core component of all API - Requests is the Action&#39;s ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.</p>
</div><div class="sc-EFWon hgVHfA"><a href="http://dev.ltep-technologies.com">LTEP Sophrosyne docs</a></div></div></div></div><div id="tag/API" data-section-id="tag/API" class="sc-eDLKkx hNzKJC"><div class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h1 class="sc-fsYfdN gqLiaw"><a class="sc-csKJxZ fNhImz" href="#tag/API" aria-label="tag/API"></a>API</h1></div></div><div class="sc-hLQSwg jSgyLg"><div class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS redoc-markdown " html="&lt;p&gt;LTEP Sophrosyne&amp;#39;s API&lt;/p&gt;
"><p>LTEP Sophrosyne&#39;s API</p>
</div></div></div><div id="tag/API/operation/executeAction" data-section-id="tag/API/operation/executeAction" class="sc-eDLKkx cSNAXN"><div data-section-id="operation/executeAction" id="operation/executeAction" class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h2 class="sc-qZrbh gwJLUj"><a class="sc-csKJxZ fNhImz" href="#tag/API/operation/executeAction" aria-label="tag/API/operation/executeAction"></a>Execute action by id<!-- --> </h2><div class="sc-eYFTNc dZbpPF"><div html="&lt;p&gt;Use this endpoint to execute an Action&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>Use this endpoint to execute an Action</p>
</div></div><div><h5 class="sc-irLvIq cnGhhy">path<!-- --> Parameters</h5><table class="sc-hIPBNq kHkWhD"><tbody><tr class=""><td kind="field" title="id" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">id</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s ID&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">apikey</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s Apikey&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-fYitVF duKVDl">Responses</h3><div><button class="sc-hsaIUA iSOCsR" disabled=""><strong class="sc-gWQvRS ePkkgX">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>successful operation</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">400<!-- --> </strong><div html="&lt;p&gt;Invalid id supplied&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Invalid id supplied</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Unauthorized</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">404<!-- --> </strong><div html="&lt;p&gt;Action not found&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Action not found</p>
</div></button></div></div></div><div class="sc-jTQCzO sc-gLLuof imiXRU jGdkPR"><div class="sc-bPrlCs cIsduN"><button class="sc-GkLId bclCVA"><span type="post" class="sc-jYnQyy jBKVIL http-verb post">post</span><span class="sc-fYrVWQ gllLir">/ext/action/{id}/apikey/{apikey}</span><svg class="sc-eTNRI exoGJA" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-eGgGjL hsEiws"><div class="sc-fnpiog jerStl"><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div><div tabindex="0" role="button"><div class="sc-lkDHyp etvaCd"><span></span>/ext/action/{id}/apikey/{apikey}</div></div></div></div></div></div></div></div><div id="tag/API/operation/executeDynamicAction" data-section-id="tag/API/operation/executeDynamicAction" class="sc-eDLKkx cSNAXN"><div data-section-id="operation/executeDynamicAction" id="operation/executeDynamicAction" class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h2 class="sc-qZrbh gwJLUj"><a class="sc-csKJxZ fNhImz" href="#tag/API/operation/executeDynamicAction" aria-label="tag/API/operation/executeDynamicAction"></a>Execute dynamic action by id<!-- --> </h2><div class="sc-eYFTNc dZbpPF"><div html="&lt;p&gt;Use this endpoint to execute a Dynamic Action by passing the parameters in the request&amp;#39;s path&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>Use this endpoint to execute a Dynamic Action by passing the parameters in the request&#39;s path</p>
</div></div><div><h5 class="sc-irLvIq cnGhhy">path<!-- --> Parameters</h5><table class="sc-hIPBNq kHkWhD"><tbody><tr class=""><td kind="field" title="id" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">id</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s ID&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s ID</p>
</div></div></div></td></tr><tr class=""><td kind="field" title="parameters" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">parameters</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><span class="sc-gUjWJS itHPsH"> <!-- -->Example:<!-- --> </span> <span class="sc-gUjWJS sc-ldgOGP itHPsH cRxwgg">execution_times:5,port:127.0.0.1</span></div><div><div html="&lt;p&gt;The passed parameters&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>The passed parameters</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">apikey</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s Apikey&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-fYitVF duKVDl">Responses</h3><div><button class="sc-hsaIUA iSOCsR" disabled=""><strong class="sc-gWQvRS ePkkgX">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>successful operation</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">400<!-- --> </strong><div html="&lt;p&gt;Invalid id supplied&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Invalid id supplied</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Unauthorized</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">404<!-- --> </strong><div html="&lt;p&gt;Dynamic Action not found&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Dynamic Action not found</p>
</div></button></div></div></div><div class="sc-jTQCzO sc-gLLuof imiXRU jGdkPR"><div class="sc-bPrlCs cIsduN"><button class="sc-GkLId bclCVA"><span type="post" class="sc-jYnQyy jBKVIL http-verb post">post</span><span class="sc-fYrVWQ gllLir">/ext/dynamicaction/{id}/parameters/{parameters}/apikey/{apikey}</span><svg class="sc-eTNRI exoGJA" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-eGgGjL hsEiws"><div class="sc-fnpiog jerStl"><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div><div tabindex="0" role="button"><div class="sc-lkDHyp etvaCd"><span></span>/ext/dynamicaction/{id}/parameters/{parameters}/apikey/{apikey}</div></div></div></div></div></div></div></div><div id="tag/API/operation/executeDynamicActionParamsInBody" data-section-id="tag/API/operation/executeDynamicActionParamsInBody" class="sc-eDLKkx cSNAXN"><div data-section-id="operation/executeDynamicActionParamsInBody" id="operation/executeDynamicActionParamsInBody" class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h2 class="sc-qZrbh gwJLUj"><a class="sc-csKJxZ fNhImz" href="#tag/API/operation/executeDynamicActionParamsInBody" aria-label="tag/API/operation/executeDynamicActionParamsInBody"></a>Execute dynamic action by id<!-- --> </h2><div class="sc-eYFTNc dZbpPF"><div html="&lt;p&gt;Use this endpoint to execute a Dynamic Action by passing the parameters as JSON in the request&amp;#39;s body&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>Use this endpoint to execute a Dynamic Action by passing the parameters as JSON in the request&#39;s body</p>
</div></div><div><h5 class="sc-irLvIq cnGhhy">path<!-- --> Parameters</h5><table class="sc-hIPBNq kHkWhD"><tbody><tr class=""><td kind="field" title="id" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">id</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s ID&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">apikey</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s Apikey&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><h5 class="sc-irLvIq cnGhhy">Request Body schema: <span class="sc-gYrqIg hJSqDi">application/json</span></h5><div html="&lt;p&gt;The parameters passed as JSON. Use the interpolated string as key and your value as value. For the below example the Dynamic Action commands looks as follows: ping -n {{execution_times}} {{port}}&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>The parameters passed as JSON. Use the interpolated string as key and your value as value. For the below example the Dynamic Action commands looks as follows: ping -n {{execution_times}} {{port}}</p>
</div><div><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">object</span></div> <div><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div></div></div></div><div><h3 class="sc-fYitVF duKVDl">Responses</h3><div><button class="sc-hsaIUA iSOCsR" disabled=""><strong class="sc-gWQvRS ePkkgX">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>successful operation</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">400<!-- --> </strong><div html="&lt;p&gt;Invalid id supplied&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Invalid id supplied</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Unauthorized</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">404<!-- --> </strong><div html="&lt;p&gt;Dynamic Action not found&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Dynamic Action not found</p>
</div></button></div></div></div><div class="sc-jTQCzO sc-gLLuof imiXRU jGdkPR"><div class="sc-bPrlCs cIsduN"><button class="sc-GkLId bclCVA"><span type="post" class="sc-jYnQyy jBKVIL http-verb post">post</span><span class="sc-fYrVWQ gllLir">/ext/dynamicaction/{id}/apikey/{apikey}</span><svg class="sc-eTNRI exoGJA" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-eGgGjL hsEiws"><div class="sc-fnpiog jerStl"><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div><div tabindex="0" role="button"><div class="sc-lkDHyp etvaCd"><span></span>/ext/dynamicaction/{id}/apikey/{apikey}</div></div></div></div></div><div><h3 class="sc-kFCroH klfnyk"> <!-- -->Request samples<!-- --> </h3><div class="sc-cyZbeP jSWvqu" data-rttabs="true"><ul class="react-tabs__tab-list" role="tablist"><li class="react-tabs__tab react-tabs__tab--selected" role="tab" id="react-tabs-0" aria-selected="true" aria-disabled="false" aria-controls="react-tabs-1" tabindex="0" data-rttab="true">Payload</li></ul><div class="react-tabs__tab-panel react-tabs__tab-panel--selected" role="tabpanel" id="react-tabs-1" aria-labelledby="react-tabs-0"><div><div class="sc-cPtzlb jBjImi"><span class="sc-bCvmQg eTZsJr">Content type</span><div class="sc-dQmiwx jCmKdj">application/json</div></div><div class="sc-hVcFVo jeLSWq"><div class="sc-cSxRuM fOJBdW"><div class="sc-gjLLEI iwAAMv"><button><div class="sc-jdHILj krcPXE">Copy</div></button></div><div class="sc-iKOmoZ WVNwY sc-jMbVJB DqFKH"><div class="redoc-json"><code><button class="collapser" aria-label="collapse"></button><span class="token punctuation">{</span><span class="ellipsis"></span><ul class="obj collapsible"><li><div class="hoverable "><span class="property token string">"execution_times"</span>: <span class="token number">5</span><span class="token punctuation">,</span></div></li><li><div class="hoverable "><span class="property token string">"port"</span>: <span class="token string">&quot;127.0.0.1&quot;</span></div></li></ul><span class="token punctuation">}</span></code></div></div></div></div></div></div></div></div></div></div></div><div id="tag/API/operation/stopAction" data-section-id="tag/API/operation/stopAction" class="sc-eDLKkx cSNAXN"><div data-section-id="operation/stopAction" id="operation/stopAction" class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h2 class="sc-qZrbh gwJLUj"><a class="sc-csKJxZ fNhImz" href="#tag/API/operation/stopAction" aria-label="tag/API/operation/stopAction"></a>Stop action execution by id<!-- --> </h2><div class="sc-eYFTNc dZbpPF"><div html="&lt;p&gt;Use this endpoint to programmatically stop a running Action&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>Use this endpoint to programmatically stop a running Action</p>
</div></div><div><h5 class="sc-irLvIq cnGhhy">path<!-- --> Parameters</h5><table class="sc-hIPBNq kHkWhD"><tbody><tr class=""><td kind="field" title="id" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">id</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s ID&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">apikey</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s Apikey&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-fYitVF duKVDl">Responses</h3><div><button class="sc-hsaIUA iSOCsR" disabled=""><strong class="sc-gWQvRS ePkkgX">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>successful operation</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">400<!-- --> </strong><div html="&lt;p&gt;Invalid id supplied&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Invalid id supplied</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Unauthorized</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">404<!-- --> </strong><div html="&lt;p&gt;Action not found&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Action not found</p>
</div></button></div></div></div><div class="sc-jTQCzO sc-gLLuof imiXRU jGdkPR"><div class="sc-bPrlCs cIsduN"><button class="sc-GkLId bclCVA"><span type="post" class="sc-jYnQyy jBKVIL http-verb post">post</span><span class="sc-fYrVWQ gllLir">/ext/action/{id}/stop/apikey/{apikey}</span><svg class="sc-eTNRI exoGJA" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-eGgGjL hsEiws"><div class="sc-fnpiog jerStl"><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div><div tabindex="0" role="button"><div class="sc-lkDHyp etvaCd"><span></span>/ext/action/{id}/stop/apikey/{apikey}</div></div></div></div></div></div></div></div><div id="tag/API/operation/stopDynamicAction" data-section-id="tag/API/operation/stopDynamicAction" class="sc-eDLKkx cSNAXN"><div data-section-id="operation/stopDynamicAction" id="operation/stopDynamicAction" class="sc-iBdnpw fsPUig"><div class="sc-hLQSwg gikxZY"><h2 class="sc-qZrbh gwJLUj"><a class="sc-csKJxZ fNhImz" href="#tag/API/operation/stopDynamicAction" aria-label="tag/API/operation/stopDynamicAction"></a>Stop dynamic action execution by id<!-- --> </h2><div class="sc-eYFTNc dZbpPF"><div html="&lt;p&gt;Use this endpoint to programmatically stop a running Dynamic Action&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS"><p>Use this endpoint to programmatically stop a running Dynamic Action</p>
</div></div><div><h5 class="sc-irLvIq cnGhhy">path<!-- --> Parameters</h5><table class="sc-hIPBNq kHkWhD"><tbody><tr class=""><td kind="field" title="id" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">id</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s ID&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s ID</p>
</div></div></div></td></tr><tr class="last "><td kind="field" title="apikey" class="sc-hABBmJ sc-fHejqy cqoAxn hfWKVF"><span class="sc-ifyrAs hIHfpT"></span><span class="property-name">apikey</span><div class="sc-gUjWJS sc-eKzvBH itHPsH ciWJhv">required</div></td><td class="sc-blmEgr berbbf"><div><div><span class="sc-gUjWJS sc-kZOsHZ itHPsH iSyacY"></span><span class="sc-gUjWJS sc-iLXxbI itHPsH gfdSsP">string</span></div> <div><div html="&lt;p&gt;Pass the Action&amp;#39;s Apikey&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"><p>Pass the Action&#39;s Apikey</p>
</div></div></div></td></tr></tbody></table></div><div><h3 class="sc-fYitVF duKVDl">Responses</h3><div><button class="sc-hsaIUA iSOCsR" disabled=""><strong class="sc-gWQvRS ePkkgX">200<!-- --> </strong><div html="&lt;p&gt;successful operation&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>successful operation</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">400<!-- --> </strong><div html="&lt;p&gt;Invalid id supplied&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Invalid id supplied</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">401<!-- --> </strong><div html="&lt;p&gt;Unauthorized&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Unauthorized</p>
</div></button></div><div><button class="sc-hsaIUA ifZPCr" disabled=""><strong class="sc-gWQvRS ePkkgX">404<!-- --> </strong><div html="&lt;p&gt;Dynamic Action not found&lt;/p&gt;
" class="sc-iKOmoZ sc-cCzLxZ WVNwY VEBGS sc-ckdEwu LxEPk"><p>Dynamic Action not found</p>
</div></button></div></div></div><div class="sc-jTQCzO sc-gLLuof imiXRU jGdkPR"><div class="sc-bPrlCs cIsduN"><button class="sc-GkLId bclCVA"><span type="post" class="sc-jYnQyy jBKVIL http-verb post">post</span><span class="sc-fYrVWQ gllLir">/ext/dynamicaction/{id}/stop/apikey/{apikey}</span><svg class="sc-eTNRI exoGJA" style="margin-right:-25px" version="1.1" viewBox="0 0 24 24" x="0" xmlns="http://www.w3.org/2000/svg" y="0" aria-hidden="true"><polygon points="17.3 8.3 12 13.6 6.7 8.3 5.3 9.7 12 16.4 18.7 9.7 "></polygon></svg></button><div aria-hidden="true" class="sc-eGgGjL hsEiws"><div class="sc-fnpiog jerStl"><div html="" class="sc-iKOmoZ sc-cCzLxZ WVNwY jaVotg"></div><div tabindex="0" role="button"><div class="sc-lkDHyp etvaCd"><span></span>/ext/dynamicaction/{id}/stop/apikey/{apikey}</div></div></div></div></div></div></div></div></div><div class="sc-juusvx bsunyy"></div></div></div>
      <script>
      const __redoc_state = {"menu":{"activeItemIdx":-1},"spec":{"data":{"openapi":"3.0.3","info":{"title":"LTEP Sophrosyne - Service API","description":"This API document describes the available LTEP Sophrosyne Action APIs.\n1. Trigger a simple Action without passing any parameters\n2. Trigger a Dynamic Action passing parameters in the path using interpolation\n3. Trigger a Dynamic Action passing parameters in the body as JSON\n\nCore component of all API - Requests is the Action's ID and a valid Apikey. Both can be obtained from your Sophrosyne Web-UI.","contact":{"email":"efstratios.pahis@ltep-technologies.com"},"license":{"name":"Apache 2.0","url":"http://www.apache.org/licenses/LICENSE-2.0.html"},"version":"1.1.0"},"externalDocs":{"description":"LTEP Sophrosyne docs","url":"http://dev.ltep-technologies.com"},"tags":[{"name":"API","description":"LTEP Sophrosyne's API"}],"paths":{"/ext/action/{id}/apikey/{apikey}":{"post":{"tags":["API"],"summary":"Execute action by id","description":"Use this endpoint to execute an Action","operationId":"executeAction","parameters":[{"name":"id","in":"path","description":"Pass the Action's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid id supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Action not found"}}}},"/ext/dynamicaction/{id}/parameters/{parameters}/apikey/{apikey}":{"post":{"tags":["API"],"summary":"Execute dynamic action by id","description":"Use this endpoint to execute a Dynamic Action by passing the parameters in the request's path","operationId":"executeDynamicAction","parameters":[{"name":"id","in":"path","description":"Pass the Action's ID","required":true,"schema":{"type":"string"}},{"name":"parameters","in":"path","description":"The passed parameters","required":true,"schema":{"type":"string","example":"execution_times:5,port:127.0.0.1"}},{"name":"apikey","in":"path","description":"Pass the Action's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid id supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Dynamic Action not found"}}}},"/ext/dynamicaction/{id}/apikey/{apikey}":{"post":{"tags":["API"],"summary":"Execute dynamic action by id","description":"Use this endpoint to execute a Dynamic Action by passing the parameters as JSON in the request's body","operationId":"executeDynamicActionParamsInBody","parameters":[{"name":"id","in":"path","description":"Pass the Action's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action's Apikey","required":true,"schema":{"type":"string"}}],"requestBody":{"description":"The parameters passed as JSON. Use the interpolated string as key and your value as value. For the below example the Dynamic Action commands looks as follows: ping -n {{execution_times}} {{port}}","content":{"application/json":{"schema":{"type":"object"},"examples":{"dynamic_action":{"value":{"execution_times":5,"port":"127.0.0.1"}}}}}},"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid id supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Dynamic Action not found"}}}},"/ext/action/{id}/stop/apikey/{apikey}":{"post":{"tags":["API"],"summary":"Stop action execution by id","description":"Use this endpoint to programmatically stop a running Action","operationId":"stopAction","parameters":[{"name":"id","in":"path","description":"Pass the Action's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid id supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Action not found"}}}},"/ext/dynamicaction/{id}/stop/apikey/{apikey}":{"post":{"tags":["API"],"summary":"Stop dynamic action execution by id","description":"Use this endpoint to programmatically stop a running Dynamic Action","operationId":"stopDynamicAction","parameters":[{"name":"id","in":"path","description":"Pass the Action's ID","required":true,"schema":{"type":"string"}},{"name":"apikey","in":"path","description":"Pass the Action's Apikey","required":true,"schema":{"type":"string"}}],"responses":{"200":{"description":"successful operation"},"400":{"description":"Invalid id supplied"},"401":{"description":"Unauthorized"},"404":{"description":"Dynamic Action not found"}}}}},"components":{}}},"searchIndex":{"store":["tag/API","tag/API/operation/executeAction","tag/API/operation/executeDynamicAction","tag/API/operation/executeDynamicActionParamsInBody","tag/API/operation/stopAction","tag/API/operation/stopDynamicAction"],"index":{"version":"2.3.9","fields":["title","description"],"fieldVectors":[["title/0",[0,1.455]],["description/0",[0,1.358,1,2.032,2,2.032]],["title/1",[3,0.173,4,0.306,5,0.256]],["description/1",[3,0.187,4,0.331,6,0.277,7,0.277,8,1.771]],["title/2",[3,0.154,4,0.272,5,0.228,9,0.07]],["description/2",[3,0.141,4,0.25,6,0.21,7,0.21,9,0.065,10,0.896,11,0.896,12,0.896,13,1.341,14,1.341]],["title/3",[3,0.154,4,0.272,5,0.228,9,0.07]],["description/3",[3,0.135,4,0.239,6,0.2,7,0.2,9,0.062,10,0.855,11,0.855,12,0.855,15,1.279,16,1.279,17,1.279]],["title/4",[3,0.154,4,0.272,5,0.228,18,0.417]],["description/4",[4,0.293,6,0.246,7,0.246,18,0.45,19,1.049,20,1.049,21,1.57]],["title/5",[3,0.138,4,0.245,5,0.205,9,0.063,18,0.376]],["description/5",[4,0.277,6,0.233,7,0.233,9,0.071,18,0.426,19,0.993,20,0.993,22,1.485]]],"invertedIndex":[["action",{"_index":4,"title":{"1":{},"2":{},"3":{},"4":{},"5":{}},"description":{"1":{},"2":{},"3":{},"4":{},"5":{}}}],["api",{"_index":0,"title":{"0":{}},"description":{"0":{}}}],["bodi",{"_index":16,"title":{},"description":{"3":{}}}],["dynam",{"_index":9,"title":{"2":{},"3":{},"5":{}},"description":{"2":{},"3":{},"5":{}}}],["endpoint",{"_index":7,"title":{},"description":{"1":{},"2":{},"3":{},"4":{},"5":{}}}],["execut",{"_index":3,"title":{"1":{},"2":{},"3":{},"4":{},"5":{}},"description":{"1":{},"2":{},"3":{}}}],["ext/action/{id}/apikey/{apikey",{"_index":8,"title":{},"description":{"1":{}}}],["ext/action/{id}/stop/apikey/{apikey",{"_index":21,"title":{},"description":{"4":{}}}],["ext/dynamicaction/{id}/apikey/{apikey",{"_index":17,"title":{},"description":{"3":{}}}],["ext/dynamicaction/{id}/parameters/{parameters}/apikey/{apikey",{"_index":14,"title":{},"description":{"2":{}}}],["ext/dynamicaction/{id}/stop/apikey/{apikey",{"_index":22,"title":{},"description":{"5":{}}}],["id",{"_index":5,"title":{"1":{},"2":{},"3":{},"4":{},"5":{}},"description":{}}],["json",{"_index":15,"title":{},"description":{"3":{}}}],["ltep",{"_index":1,"title":{},"description":{"0":{}}}],["paramet",{"_index":11,"title":{},"description":{"2":{},"3":{}}}],["pass",{"_index":10,"title":{},"description":{"2":{},"3":{}}}],["path",{"_index":13,"title":{},"description":{"2":{}}}],["programmat",{"_index":19,"title":{},"description":{"4":{},"5":{}}}],["request'",{"_index":12,"title":{},"description":{"2":{},"3":{}}}],["run",{"_index":20,"title":{},"description":{"4":{},"5":{}}}],["sophrosyne'",{"_index":2,"title":{},"description":{"0":{}}}],["stop",{"_index":18,"title":{"4":{},"5":{}},"description":{"4":{},"5":{}}}],["us",{"_index":6,"title":{},"description":{"1":{},"2":{},"3":{},"4":{},"5":{}}}]],"pipeline":[]}},"options":{}};

      var container = document.getElementById('redoc');
      Redoc.hydrate(__redoc_state, container);

      </script>
</body>

</html>