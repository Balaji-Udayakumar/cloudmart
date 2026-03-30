# CloudMart — AI-Integrated Multi-Cloud E-Commerce Platform

[![AWS](https://img.shields.io/badge/AWS-EKS%20%7C%20DynamoDB%20%7C%20Bedrock%20%7C%20Lambda-FF9900?logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-412991?logo=openai&logoColor=white)](https://openai.com)
[![Azure](https://img.shields.io/badge/Azure-AI%20Language-0078D4?logo=microsoftazure&logoColor=white)](https://azure.microsoft.com)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-BigQuery-4285F4?logo=googlecloud&logoColor=white)](https://cloud.google.com)
[![Terraform](https://img.shields.io/badge/Terraform-Infrastructure%20as%20Code-7B42BC?logo=terraform&logoColor=white)](https://terraform.io)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-EKS-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io)

CloudMart is a production-grade e-commerce prototype that demonstrates how modern AI capabilities and multi-cloud infrastructure work together in a single, unified application. Built during graduate research at the University of Maryland, it serves as a hands-on reference for integrating generative AI, automated CI/CD pipelines, and cross-cloud data engineering.

---

## Architecture Overview

<svg width="100%" viewBox="0 0 680 560" xmlns="http://www.w3.org/2000/svg">
<defs>
  <marker id="arrow" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
    <path d="M2 1L8 5L2 9" fill="none" stroke="context-stroke" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
  </marker>
<mask id="imagine-text-gaps-m9y3ux" maskUnits="userSpaceOnUse"><rect x="0" y="0" width="680" height="560" fill="white"/><rect x="47.85359191894531" y="26.736059188842773" width="54.292823791503906" height="20.527881622314453" fill="black" rx="2"/><rect x="35.44661331176758" y="43.916622161865234" width="79.10678100585938" height="18.16675567626953" fill="black" rx="2"/><rect x="576.5623779296875" y="26.736059188842773" width="56.87530517578125" height="20.527881622314453" fill="black" rx="2"/><rect x="555.3897094726562" y="43.916622161865234" width="99.22062683105469" height="18.16675567626953" fill="black" rx="2"/><rect x="32" y="97.7360610961914" width="88.44061279296875" height="20.527881622314453" fill="black" rx="2"/><rect x="48" y="408.9166564941406" width="40.768001556396484" height="18.16675567626953" fill="black" rx="2"/><rect x="108.73480224609375" y="408.9166564941406" width="82.5304183959961" height="18.16675567626953" fill="black" rx="2"/><rect x="225.91757202148438" y="408.9166564941406" width="66.16486358642578" height="18.16675567626953" fill="black" rx="2"/><rect x="335.2091369628906" y="408.9166564941406" width="31.581745147705078" height="18.16675567626953" fill="black" rx="2"/><rect x="48" y="131.73606872558594" width="85.5113296508789" height="20.527881622314453" fill="black" rx="2"/><rect x="76.89639282226562" y="162.73606872558594" width="40.20723342895508" height="20.527881622314453" fill="black" rx="2"/><rect x="64.1204833984375" y="178.73606872558594" width="65.7590446472168" height="20.527881622314453" fill="black" rx="2"/><rect x="72.19816589355469" y="226.73606872558594" width="67.60367202758789" height="20.527881622314453" fill="black" rx="2"/><rect x="53.16158676147461" y="243.9166259765625" width="105.67682647705078" height="18.16675567626953" fill="black" rx="2"/><rect x="209.5226287841797" y="226.73606872558594" width="64.95478439331055" height="20.527881622314453" fill="black" rx="2"/><rect x="182.81976318359375" y="243.9166259765625" width="118.36050415039062" height="18.16675567626953" fill="black" rx="2"/><rect x="117.94371032714844" y="335.9166259765625" width="104.11257934570312" height="18.16675567626953" fill="black" rx="2"/><rect x="357.15167236328125" y="162.73606872558594" width="81.69664001464844" height="20.527881622314453" fill="black" rx="2"/><rect x="321.9561462402344" y="179.9166259765625" width="152.08770751953125" height="18.16675567626953" fill="black" rx="2"/><rect x="367.5111083984375" y="226.73606872558594" width="60.97776412963867" height="20.527881622314453" fill="black" rx="2"/><rect x="333.3411865234375" y="243.9166259765625" width="129.3176040649414" height="18.16675567626953" fill="black" rx="2"/><rect x="366.57403564453125" y="290.7360534667969" width="62.851905822753906" height="20.527881622314453" fill="black" rx="2"/><rect x="347.15008544921875" y="307.9166259765625" width="101.6998062133789" height="18.16675567626953" fill="black" rx="2"/><rect x="356.5614013671875" y="355.7360534667969" width="82.87720489501953" height="20.527881622314453" fill="black" rx="2"/><rect x="504" y="131.73606872558594" width="97.33910369873047" height="20.527881622314453" fill="black" rx="2"/><rect x="540.2943115234375" y="156.73605346679688" width="69.41141128540039" height="20.527881622314453" fill="black" rx="2"/><rect x="517.1441650390625" y="173.9166259765625" width="115.71161651611328" height="18.16675567626953" fill="black" rx="2"/><rect x="504" y="231.736083984375" width="113.05535125732422" height="20.527881622314453" fill="black" rx="2"/><rect x="508.96142578125" y="256.7360534667969" width="132.0771713256836" height="20.527881622314453" fill="black" rx="2"/><rect x="517.9963989257812" y="273.9166259765625" width="114.0071792602539" height="18.16675567626953" fill="black" rx="2"/><rect x="33.434913635253906" y="466.736083984375" width="73.13018035888672" height="20.527881622314453" fill="black" rx="2"/><rect x="29.284496307373047" y="483.9166564941406" width="81.43101501464844" height="18.16675567626953" fill="black" rx="2"/><rect x="66.00000762939453" y="504.9166259765625" width="73.46959686279297" height="18.16675567626953" fill="black" rx="2"/><rect x="190" y="504.9166259765625" width="100.17243957519531" height="18.16675567626953" fill="black" rx="2"/></mask></defs>

<!-- GitHub (top-left external) -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="20" y="20" width="110" height="44" rx="8" stroke-width="0.5" style="fill:rgb(241, 239, 232);stroke:rgb(95, 94, 90);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="75" y="37" text-anchor="middle" dominant-baseline="central" style="fill:rgb(68, 68, 65);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">GitHub</text>
  <text x="75" y="53" text-anchor="middle" dominant-baseline="central" style="fill:rgb(95, 94, 90);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Source code</text>
</g>

<!-- OpenAI (top-right external) -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="550" y="20" width="110" height="44" rx="8" stroke-width="0.5" style="fill:rgb(234, 243, 222);stroke:rgb(59, 109, 17);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="605" y="37" text-anchor="middle" dominant-baseline="central" style="fill:rgb(39, 80, 10);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">OpenAI</text>
  <text x="605" y="53" text-anchor="middle" dominant-baseline="central" style="fill:rgb(59, 109, 17);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">GPT-4o support</text>
</g>

<!-- AWS Region outer container -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="20" y="86" width="450" height="360" rx="16" stroke-width="0.5" fill-opacity="0.12" style="fill:rgb(250, 238, 218);stroke:rgb(133, 79, 11);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
</g>
<text x="36" y="108" dominant-baseline="central" style="fill:rgb(20, 20, 19);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:start;dominant-baseline:central">AWS Region</text>

<!-- CI/CD dashed inner box -->
<rect x="36" y="400" width="420" height="36" rx="8" fill="none" stroke-dasharray="4 3" stroke-width="0.5" stroke="var(--color-border-secondary)" style="fill:none;stroke:rgba(31, 30, 29, 0.3);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-dasharray:4px, 3px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
<text x="52" y="418" dominant-baseline="central" style="fill:rgb(61, 61, 58);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:start;dominant-baseline:central">CI/CD</text>

<!-- CodePipeline -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="100" y="404" width="100" height="28" rx="6" stroke-width="0.5" style="fill:rgb(250, 238, 218);stroke:rgb(133, 79, 11);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="150" y="418" text-anchor="middle" dominant-baseline="central" style="fill:rgb(133, 79, 11);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">CodePipeline</text>
</g>

<!-- CodeBuild -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="214" y="404" width="90" height="28" rx="6" stroke-width="0.5" style="fill:rgb(250, 238, 218);stroke:rgb(133, 79, 11);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="259" y="418" text-anchor="middle" dominant-baseline="central" style="fill:rgb(133, 79, 11);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">CodeBuild</text>
</g>

<!-- ECR -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="318" y="404" width="66" height="28" rx="6" stroke-width="0.5" style="fill:rgb(250, 238, 218);stroke:rgb(133, 79, 11);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="351" y="418" text-anchor="middle" dominant-baseline="central" style="fill:rgb(133, 79, 11);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">ECR</text>
</g>

<!-- EKS Cluster container -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="36" y="120" width="270" height="260" rx="12" stroke-width="0.5" fill-opacity="0.12" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
</g>
<text x="52" y="142" dominant-baseline="central" style="fill:rgb(20, 20, 19);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:start;dominant-baseline:central">EKS Cluster</text>

<!-- Load Balancer -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="52" y="156" width="90" height="44" rx="8" stroke-width="0.5" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="97" y="173" text-anchor="middle" dominant-baseline="central" style="fill:rgb(12, 68, 124);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Load</text>
  <text x="97" y="189" text-anchor="middle" dominant-baseline="central" style="fill:rgb(12, 68, 124);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Balancer</text>
</g>

<!-- Frontend pod -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="52" y="220" width="108" height="44" rx="8" stroke-width="0.5" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="106" y="237" text-anchor="middle" dominant-baseline="central" style="fill:rgb(12, 68, 124);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Frontend</text>
  <text x="106" y="253" text-anchor="middle" dominant-baseline="central" style="fill:rgb(24, 95, 165);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">React / port 5001</text>
</g>

<!-- Backend pod -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="188" y="220" width="108" height="44" rx="8" stroke-width="0.5" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="242" y="237" text-anchor="middle" dominant-baseline="central" style="fill:rgb(12, 68, 124);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Backend</text>
  <text x="242" y="253" text-anchor="middle" dominant-baseline="central" style="fill:rgb(24, 95, 165);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Node.js / port 5000</text>
</g>

<!-- Kubernetes label -->
<text x="170" y="345" text-anchor="middle" dominant-baseline="central" style="fill:rgb(61, 61, 58);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Kubernetes pods</text>

<!-- DynamoDB -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="340" y="156" width="116" height="44" rx="8" stroke-width="0.5" style="fill:rgb(238, 237, 254);stroke:rgb(83, 74, 183);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="398" y="173" text-anchor="middle" dominant-baseline="central" style="fill:rgb(60, 52, 137);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">DynamoDB</text>
  <text x="398" y="189" text-anchor="middle" dominant-baseline="central" style="fill:rgb(83, 74, 183);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Products, Orders, Tickets</text>
</g>

<!-- Lambda -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="340" y="220" width="116" height="44" rx="8" stroke-width="0.5" style="fill:rgb(238, 237, 254);stroke:rgb(83, 74, 183);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="398" y="237" text-anchor="middle" dominant-baseline="central" style="fill:rgb(60, 52, 137);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Lambda</text>
  <text x="398" y="253" text-anchor="middle" dominant-baseline="central" style="fill:rgb(83, 74, 183);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Products + streaming</text>
</g>

<!-- Bedrock -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="340" y="284" width="116" height="44" rx="8" stroke-width="0.5" style="fill:rgb(238, 237, 254);stroke:rgb(83, 74, 183);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="398" y="301" text-anchor="middle" dominant-baseline="central" style="fill:rgb(60, 52, 137);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Bedrock</text>
  <text x="398" y="317" text-anchor="middle" dominant-baseline="central" style="fill:rgb(83, 74, 183);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Claude 3 Sonnet</text>
</g>

<!-- S3 -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="340" y="348" width="116" height="36" rx="8" stroke-width="0.5" style="fill:rgb(238, 237, 254);stroke:rgb(83, 74, 183);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="398" y="366" text-anchor="middle" dominant-baseline="central" style="fill:rgb(60, 52, 137);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Amazon S3</text>
</g>

<!-- Google Cloud panel -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="490" y="120" width="170" height="80" rx="12" stroke-width="0.5" fill-opacity="0.15" style="fill:rgb(225, 245, 238);stroke:rgb(15, 110, 86);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
</g>
<text x="508" y="142" dominant-baseline="central" style="fill:rgb(20, 20, 19);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:start;dominant-baseline:central">Google Cloud</text>
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="506" y="154" width="138" height="36" rx="8" stroke-width="0.5" style="fill:rgb(225, 245, 238);stroke:rgb(15, 110, 86);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="575" y="167" text-anchor="middle" dominant-baseline="central" style="fill:rgb(8, 80, 65);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">BigQuery</text>
  <text x="575" y="183" text-anchor="middle" dominant-baseline="central" style="fill:rgb(15, 110, 86);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Real-time analytics</text>
</g>

<!-- Azure panel -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="490" y="220" width="170" height="80" rx="12" stroke-width="0.5" fill-opacity="0.1" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
</g>
<text x="508" y="242" dominant-baseline="central" style="fill:rgb(20, 20, 19);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:start;dominant-baseline:central">Microsoft Azure</text>
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="506" y="254" width="138" height="36" rx="8" stroke-width="0.5" style="fill:rgb(230, 241, 251);stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="575" y="267" text-anchor="middle" dominant-baseline="central" style="fill:rgb(12, 68, 124);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Azure AI Language</text>
  <text x="575" y="283" text-anchor="middle" dominant-baseline="central" style="fill:rgb(24, 95, 165);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Sentiment analysis</text>
</g>

<!-- Terraform (bottom left external) -->
<g style="fill:rgb(0, 0, 0);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto">
  <rect x="20" y="464" width="100" height="36" rx="8" stroke-width="0.5" style="fill:rgb(238, 237, 254);stroke:rgb(83, 74, 183);color:rgb(0, 0, 0);stroke-width:0.5px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
  <text x="70" y="477" text-anchor="middle" dominant-baseline="central" style="fill:rgb(60, 52, 137);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:14px;font-weight:500;text-anchor:middle;dominant-baseline:central">Terraform</text>
  <text x="70" y="493" text-anchor="middle" dominant-baseline="central" style="fill:rgb(83, 74, 183);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:middle;dominant-baseline:central">Infra as code</text>
</g>

<!-- ARROWS -->
<!-- GitHub -> CodePipeline -->
<path d="M75 64 L75 418 L98 418" fill="none" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:none;stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- CodePipeline -> CodeBuild -->
<line x1="200" y1="418" x2="212" y2="418" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- CodeBuild -> ECR -->
<line x1="304" y1="418" x2="316" y2="418" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- ECR -> EKS (up) -->
<path d="M351 404 L351 380 L170 380 L170 266" fill="none" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:none;stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Load Balancer -> Frontend -->
<line x1="97" y1="200" x2="106" y2="218" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Load Balancer -> Backend -->
<path d="M142 178 L242 178 L242 218" fill="none" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:none;stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Backend -> DynamoDB -->
<line x1="296" y1="242" x2="338" y2="178" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Backend -> Lambda -->
<line x1="296" y1="248" x2="338" y2="242" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Backend -> Bedrock -->
<line x1="296" y1="256" x2="338" y2="306" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- DynamoDB -> Lambda stream -->
<line x1="398" y1="200" x2="398" y2="218" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Lambda -> BigQuery -->
<path d="M456 237 L575 237 L575 252" fill="none" stroke="#1D9E75" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:none;stroke:rgb(29, 158, 117);color:rgb(0, 0, 0);stroke-width:1px;stroke-dasharray:4px, 3px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Backend -> Azure -->
<path d="M296 260 L490 270" fill="none" stroke="#185FA5" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#arrow)" mask="url(#imagine-text-gaps-m9y3ux)" style="fill:none;stroke:rgb(24, 95, 165);color:rgb(0, 0, 0);stroke-width:1px;stroke-dasharray:4px, 3px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Backend -> OpenAI -->
<path d="M242 220 L242 80 L548 42" fill="none" stroke="#3B6D11" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#arrow)" style="fill:none;stroke:rgb(59, 109, 17);color:rgb(0, 0, 0);stroke-width:1px;stroke-dasharray:4px, 3px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>

<!-- Legend -->
<line x1="36" y1="510" x2="64" y2="510" stroke="var(--color-border-primary)" stroke-width="1" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgba(31, 30, 29, 0.4);color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
<text x="70" y="514" dominant-baseline="central" style="fill:rgb(61, 61, 58);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:start;dominant-baseline:central">Internal call</text>
<line x1="160" y1="510" x2="188" y2="510" stroke="#1D9E75" stroke-width="1" stroke-dasharray="4 3" marker-end="url(#arrow)" style="fill:rgb(0, 0, 0);stroke:rgb(29, 158, 117);color:rgb(0, 0, 0);stroke-width:1px;stroke-dasharray:4px, 3px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:16px;font-weight:400;text-anchor:start;dominant-baseline:auto"/>
<text x="194" y="514" dominant-baseline="central" style="fill:rgb(61, 61, 58);stroke:none;color:rgb(0, 0, 0);stroke-width:1px;stroke-linecap:butt;stroke-linejoin:miter;opacity:1;font-family:&quot;Anthropic Sans&quot;, -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, sans-serif;font-size:12px;font-weight:400;text-anchor:start;dominant-baseline:central">Cross-cloud call</text>
</svg>

---

## Features

### AI Capabilities

| Feature | Provider | Model | Purpose |
|---|---|---|---|
| Product Recommendations | Amazon Bedrock | Claude 3 Sonnet | Conversational product discovery with live catalog queries |
| Customer Support | OpenAI | GPT-4o | Handles general customer service and platform questions |
| Sentiment Analysis | Microsoft Azure | Azure AI Language | Classifies customer conversations as positive, neutral, or negative |

### Infrastructure & DevOps

- **Kubernetes on EKS** — Frontend and backend deployed as separate containerized pods with LoadBalancer services
- **CI/CD Pipeline** — GitHub → CodePipeline → CodeBuild → ECR → EKS. Zero-touch deployments on every push
- **Infrastructure as Code** — All AWS resources (DynamoDB, Lambda, IAM roles, EKS configuration) defined in Terraform
- **Real-time Data Streaming** — DynamoDB Streams → Lambda → Google BigQuery for live order analytics

---

## Tech Stack

### AWS Services
- **EKS (Elastic Kubernetes Service)** — Container orchestration for frontend and backend
- **DynamoDB** — NoSQL database for products, orders, and support tickets
- **Lambda** — Serverless functions for product catalog queries (Bedrock agent) and BigQuery streaming
- **Bedrock** — Managed generative AI service hosting the Claude 3 Sonnet recommendation agent
- **ECR (Elastic Container Registry)** — Docker image storage
- **CodePipeline + CodeBuild** — CI/CD automation
- **S3** — Static asset storage
- **IAM** — Role-based access control for all services

### Application
- **Frontend** — React (Vite), served on port 5001
- **Backend** — Node.js (Express), running on port 5000
- **Containerization** — Docker, with multi-stage builds for the frontend

### AI & External Services
- **Amazon Bedrock** — Hosts the Claude 3 Sonnet recommendation agent with a custom action group connected to Lambda
- **OpenAI API** — GPT-4o assistant for customer support, configured with CloudMart-specific instructions
- **Azure AI Language** — Sentiment analysis API integrated into the support chat pipeline
- **Google BigQuery** — Serverless analytics warehouse receiving real-time order streams

### Infrastructure as Code
- **Terraform** — Provisions DynamoDB tables, Lambda functions, IAM roles, Lambda event source mappings, and Bedrock agent permissions

---

## Project Structure

```
cloudmart/
├── terraform-project/
│   └── main.tf                    # All AWS infrastructure
├── challenge-day2/
│   ├── backend/
│   │   ├── Dockerfile
│   │   ├── cloudmart-backend.yaml  # Kubernetes deployment
│   │   ├── .env                    # Runtime config (Bedrock, OpenAI, Azure)
│   │   └── src/
│   │       └── lambda/
│   │           ├── list_products/  # Lambda for Bedrock agent
│   │           └── addToBigQuery/  # Lambda for DynamoDB → BigQuery stream
│   └── frontend/
│       ├── Dockerfile
│       ├── cloudmart-frontend.yaml # Kubernetes deployment
│       └── .env                    # VITE_API_BASE_URL
```

---

## How It Works

### Product Recommendation Flow

1. Customer opens the recommendation chat on the CloudMart storefront
2. The frontend sends the message to the Node.js backend
3. The backend calls the Amazon Bedrock agent (Claude 3 Sonnet)
4. The Bedrock agent invokes a Lambda function to query DynamoDB for live product data
5. Claude synthesizes the results and returns a personalized recommendation
6. The customer sees a conversational, context-aware response

### CI/CD Deployment Flow

1. Developer pushes code to the `cloudmart` GitHub repository
2. AWS CodePipeline detects the change and triggers a build
3. CodeBuild builds a Docker image using the project Dockerfile
4. The image is tagged and pushed to Amazon ECR
5. CodeBuild runs `kubectl apply` to deploy the new image to EKS
6. Kubernetes performs a rolling update — zero downtime

### Real-time Order Streaming

1. A customer places an order, which is written to the DynamoDB `cloudmart-orders` table
2. DynamoDB Streams captures the new record and triggers the `dynamodb-to-bigquery` Lambda function
3. The Lambda function authenticates to Google Cloud using a service account and writes the record to BigQuery
4. The data is immediately available for analytics queries in BigQuery

---

## Environment Variables

### Backend (`.env`)

```env
PORT=5000
AWS_REGION=us-east-1
BEDROCK_AGENT_ID=<your-bedrock-agent-id>
BEDROCK_AGENT_ALIAS_ID=<your-bedrock-agent-alias-id>
OPENAI_API_KEY=<your-openai-api-key>
OPENAI_ASSISTANT_ID=<your-openai-assistant-id>
AZURE_ENDPOINT=<your-azure-endpoint>
AZURE_API_KEY=<your-azure-api-key>
```

### Frontend (`.env`)

```env
VITE_API_BASE_URL=http://<kubernetes-backend-loadbalancer-url>:5000/api
```

---

## Setup & Deployment

### Prerequisites

- AWS account with CLI configured
- Terraform installed
- Docker installed
- `kubectl` and `eksctl` installed
- Google Cloud project with BigQuery enabled
- Azure account with Text Analytics resource
- OpenAI account with API key

### 1. Provision Infrastructure with Terraform

```bash
cd terraform-project
terraform init
terraform apply
```

This creates DynamoDB tables, Lambda functions, IAM roles, and Lambda event source mappings.

### 2. Create the EKS Cluster

```bash
eksctl create cluster \
  --name cloudmart \
  --region us-east-1 \
  --nodegroup-name standard-workers \
  --node-type t3.medium \
  --nodes 1 \
  --with-oidc \
  --managed

aws eks update-kubeconfig --name cloudmart
```

### 3. Configure the Amazon Bedrock Agent

- Enable Claude 3 Sonnet model access in the Bedrock console
- Create an agent named `cloudmart-product-recommendation-agent`
- Attach the `Get-Product-Recommendations` action group connected to the `cloudmart-list-products` Lambda function
- Create an alias named `cloudmart-prod`
- Note the Agent ID and Alias ID for backend configuration

### 4. Configure OpenAI Assistant

- Create a new assistant in the OpenAI platform with model `gpt-4o`
- Name it `CloudMart Customer Support`
- Configure instructions to handle CloudMart-specific support scenarios
- Note the Assistant ID and generate an API key

### 5. Set Up Azure Sentiment Analysis

- Create a Text Analytics resource in Azure
- Note the endpoint URL and API key

### 6. Build and Deploy Backend

```bash
cd challenge-day2/backend

# Build and push to ECR (follow ECR push commands from AWS console)
docker build -t cloudmart-backend .
# tag and push...

# Update cloudmart-backend.yaml with your Bedrock, OpenAI, and Azure credentials
kubectl apply -f cloudmart-backend.yaml
kubectl get service cloudmart-backend-app-service  # note the external URL
```

### 7. Build and Deploy Frontend

```bash
cd challenge-day2/frontend

# Update .env with the backend service URL from step 6
echo "VITE_API_BASE_URL=http://<backend-url>:5000/api" > .env

# Build and push to ECR, then deploy
kubectl apply -f cloudmart-frontend.yaml
kubectl get service cloudmart-frontend-app-service  # your app URL
```

### 8. Set Up CI/CD Pipeline

- Push your code to a GitHub repository named `cloudmart`
- In AWS CodePipeline, create `cloudmart-cicd-pipeline` connected to your GitHub repo
- Create a CodeBuild project `cloudmartBuild` with the provided `buildspec.yml`
- Create a deployment CodeBuild project `cloudmartDeployToProduction` with deploy `buildspec.yml`

---

## Teardown

To avoid ongoing AWS charges:

```bash
# Delete Kubernetes resources
kubectl delete -f cloudmart-frontend.yaml
kubectl delete -f cloudmart-backend.yaml

# Delete EKS cluster
eksctl delete cluster --name cloudmart --region us-east-1

# Destroy Terraform-managed resources
cd terraform-project
terraform destroy
```

---

## Key Learnings

This project demonstrates several cross-domain concepts in a single working system:

- **Agentic AI** — How a Bedrock agent with an action group can query live data and make decisions within a conversation
- **Multi-cloud integration** — How AWS, Azure, Google Cloud, and OpenAI services can be composed into one application without vendor lock-in
- **Event-driven streaming** — How DynamoDB Streams and Lambda enable real-time data movement without batch jobs
- **GitOps / CI/CD** — How a single `git push` can trigger a complete build and deployment pipeline
- **Infrastructure as Code** — How Terraform enables reproducible, version-controlled cloud infrastructure

---

## Acknowledgements

Developed as part of graduate-level research and coursework at the **University of Maryland, College Park** (Master of Science in Information Systems). This project was designed to serve as a practical, production-grade reference for students learning cloud architecture, DevOps, and AI integration.

---

## License

MIT
