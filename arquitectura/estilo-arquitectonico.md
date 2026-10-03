## Diagrama de arquitectura

<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 910 655" font-family="Arial, Helvetica, sans-serif" font-size="8">
<defs>
<marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M0,0 L10,5 L0,10 z" fill="#333"/></marker>
<marker id="ag" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto"><path d="M0,0 L10,5 L0,10 z" fill="#38761d"/></marker>
</defs>
<rect x="2" y="2" width="906" height="651" fill="#fff" stroke="#333"/>
<rect x="318" y="20" width="16" height="34" fill="#fff" stroke="#333"/><text x="342" y="40" font-size="9">Cliente</text>
<line x1="326" y1="54" x2="326" y2="70" stroke="#333"/>
<rect x="418" y="20" width="16" height="34" fill="#fff" stroke="#333"/><text x="442" y="40" font-size="9">Seller</text>
<line x1="426" y1="54" x2="426" y2="70" stroke="#333"/>
<rect x="517" y="20" width="16" height="34" fill="#fff" stroke="#333"/><text x="541" y="40" font-size="9">Administrador</text>
<line x1="525" y1="54" x2="525" y2="70" stroke="#333"/>
<line x1="326" y1="70" x2="525" y2="70" stroke="#333"/><line x1="432" y1="70" x2="432" y2="88" stroke="#333" marker-end="url(#ar)"/>
<rect x="284" y="88" width="297" height="33" rx="2" fill="#fff" stroke="#333"/><text x="432" y="102" text-anchor="middle" font-weight="bold" font-size="10">Cliente Web</text><text x="432" y="114" text-anchor="middle" font-size="8">[Navegador · HTML / CSS / JavaScript]</text>
<line x1="432" y1="121" x2="432" y2="193" stroke="#333" marker-end="url(#ar)"/><text x="432" y="145" text-anchor="middle" font-size="8" fill="#333" stroke="#fff" stroke-width="3" paint-order="stroke">HTTPS · JSON</text><text x="432" y="157" text-anchor="middle" font-size="8" fill="#333" stroke="#fff" stroke-width="3" paint-order="stroke">/api/v1/*</text>
<rect x="10" y="153" width="738" height="377" fill="none" stroke="#333" stroke-dasharray="6,4"/>
<text x="17" y="165" font-size="9"><tspan font-weight="bold">«monolito» Marketplace Backend</tspan> [Node.js 20 LTS · Express]</text><text x="17" y="175" font-size="8" fill="#555">Una sola aplicación · un solo proceso · un solo despliegue</text>
<rect x="22" y="187" width="714" height="130" fill="#e4ebf8" stroke="#aebfe0"/>
<text x="29" y="234" font-weight="bold" font-size="8.5">1. CAPA DE</text>
<text x="29" y="245" font-weight="bold" font-size="8.5">PRESENTACIÓN</text>
<text x="29" y="260" font-size="7" fill="#444">Recibe peticiones HTTP,</text>
<text x="29" y="270" font-size="7" fill="#444">autentica, valida la entrada</text>
<text x="29" y="280" font-size="7" fill="#444">y responde JSON</text>
<rect x="22" y="321" width="714" height="88" fill="#e3f0dc" stroke="#b5d3a6"/>
<text x="29" y="347" font-weight="bold" font-size="8.5">2. CAPA DE LÓGICA</text>
<text x="29" y="358" font-weight="bold" font-size="8.5">DE NEGOCIO</text>
<text x="29" y="373" font-size="7" fill="#444">Reglas de negocio y</text>
<text x="29" y="383" font-size="7" fill="#444">coordinación entre módulos</text>
<rect x="22" y="415" width="714" height="105" fill="#fdf0d9" stroke="#e6cf9f"/>
<text x="29" y="449.5" font-weight="bold" font-size="8.5">3. CAPA DE DATOS</text>
<text x="29" y="464.5" font-size="7" fill="#444">Persistencia y consultas a</text>
<text x="29" y="474.5" font-size="7" fill="#444">la base de datos</text>
<rect x="124" y="195" width="604" height="20" fill="#dbe5f8" stroke="#3b5b9d"/><text x="426" y="208" text-anchor="middle" font-size="8"><tspan font-weight="bold">Middlewares Express (transversales)</tspan>  cors · express.json() · auth (JWT) · validación de entrada · manejo de errores · logger</text>
<rect x="128" y="222" width="110" height="246" fill="none" stroke="#38761d" stroke-dasharray="3,3"/>
<text x="183" y="232" text-anchor="middle" font-weight="bold" font-size="8.5">módulo usuarios</text><text x="183" y="240" text-anchor="middle" font-size="6.5" fill="#555">src/modules/usuarios/</text>
<rect x="140" y="246" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="183" y="258" text-anchor="middle" font-size="7.5">usuarios.routes.js</text>
<line x1="183" y1="265" x2="183" y2="278" stroke="#333" marker-end="url(#ar)"/>
<rect x="140" y="279" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="183" y="291" text-anchor="middle" font-size="7.5">usuarios.controller.js</text>
<line x1="183" y1="298" x2="183" y2="338" stroke="#333" marker-end="url(#ar)"/>
<rect x="140" y="340" width="86" height="30" fill="#d3e5c8" stroke="#38761d"/><text x="183" y="353" text-anchor="middle" font-weight="bold" font-size="7.5">usuarios.service.js</text><text x="183" y="363" text-anchor="middle" font-size="6.5">registro, login, roles</text>
<line x1="183" y1="370" x2="183" y2="428" stroke="#333" marker-end="url(#ar)"/>
<rect x="140" y="430" width="86" height="20" fill="#fff" stroke="#bf9000"/><text x="183" y="443" text-anchor="middle" font-size="7.5">usuarios.repository.js</text>
<line x1="183" y1="450" x2="183" y2="476" stroke="#333" marker-end="url(#ar)"/>
<rect x="250" y="222" width="110" height="246" fill="none" stroke="#38761d" stroke-dasharray="3,3"/>
<text x="305" y="232" text-anchor="middle" font-weight="bold" font-size="8.5">módulo sellers</text><text x="305" y="240" text-anchor="middle" font-size="6.5" fill="#555">src/modules/sellers/</text>
<rect x="262" y="246" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="305" y="258" text-anchor="middle" font-size="7.5">sellers.routes.js</text>
<line x1="305" y1="265" x2="305" y2="278" stroke="#333" marker-end="url(#ar)"/>
<rect x="262" y="279" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="305" y="291" text-anchor="middle" font-size="7.5">sellers.controller.js</text>
<line x1="305" y1="298" x2="305" y2="338" stroke="#333" marker-end="url(#ar)"/>
<rect x="262" y="340" width="86" height="30" fill="#d3e5c8" stroke="#38761d"/><text x="305" y="353" text-anchor="middle" font-weight="bold" font-size="7.5">sellers.service.js</text><text x="305" y="363" text-anchor="middle" font-size="6.5">alta de tiendas, validación</text>
<line x1="305" y1="370" x2="305" y2="428" stroke="#333" marker-end="url(#ar)"/>
<rect x="262" y="430" width="86" height="20" fill="#fff" stroke="#bf9000"/><text x="305" y="443" text-anchor="middle" font-size="7.5">sellers.repository.js</text>
<line x1="305" y1="450" x2="305" y2="476" stroke="#333" marker-end="url(#ar)"/>
<rect x="372" y="222" width="110" height="246" fill="none" stroke="#38761d" stroke-dasharray="3,3"/>
<text x="427" y="232" text-anchor="middle" font-weight="bold" font-size="8.5">módulo catalogo</text><text x="427" y="240" text-anchor="middle" font-size="6.5" fill="#555">src/modules/catalogo/</text>
<rect x="384" y="246" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="427" y="258" text-anchor="middle" font-size="7.5">catalogo.routes.js</text>
<line x1="427" y1="265" x2="427" y2="278" stroke="#333" marker-end="url(#ar)"/>
<rect x="384" y="279" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="427" y="291" text-anchor="middle" font-size="7.5">catalogo.controller.js</text>
<line x1="427" y1="298" x2="427" y2="338" stroke="#333" marker-end="url(#ar)"/>
<rect x="384" y="340" width="86" height="30" fill="#d3e5c8" stroke="#38761d"/><text x="427" y="353" text-anchor="middle" font-weight="bold" font-size="7.5">catalogo.service.js</text><text x="427" y="363" text-anchor="middle" font-size="6.5">productos, categorías, stock</text>
<line x1="427" y1="370" x2="427" y2="428" stroke="#333" marker-end="url(#ar)"/>
<rect x="384" y="430" width="86" height="20" fill="#fff" stroke="#bf9000"/><text x="427" y="443" text-anchor="middle" font-size="7.5">catalogo.repository.js</text>
<line x1="427" y1="450" x2="427" y2="476" stroke="#333" marker-end="url(#ar)"/>
<rect x="493" y="222" width="110" height="246" fill="none" stroke="#38761d" stroke-dasharray="3,3"/>
<text x="548" y="232" text-anchor="middle" font-weight="bold" font-size="8.5">módulo carrito</text><text x="548" y="240" text-anchor="middle" font-size="6.5" fill="#555">src/modules/carrito/</text>
<rect x="505" y="246" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="548" y="258" text-anchor="middle" font-size="7.5">carrito.routes.js</text>
<line x1="548" y1="265" x2="548" y2="278" stroke="#333" marker-end="url(#ar)"/>
<rect x="505" y="279" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="548" y="291" text-anchor="middle" font-size="7.5">carrito.controller.js</text>
<line x1="548" y1="298" x2="548" y2="338" stroke="#333" marker-end="url(#ar)"/>
<rect x="505" y="340" width="86" height="30" fill="#d3e5c8" stroke="#38761d"/><text x="548" y="353" text-anchor="middle" font-weight="bold" font-size="7.5">carrito.service.js</text><text x="548" y="363" text-anchor="middle" font-size="6.5">ítems, totales</text>
<line x1="548" y1="370" x2="548" y2="428" stroke="#333" marker-end="url(#ar)"/>
<rect x="505" y="430" width="86" height="20" fill="#fff" stroke="#bf9000"/><text x="548" y="443" text-anchor="middle" font-size="7.5">carrito.repository.js</text>
<line x1="548" y1="450" x2="548" y2="476" stroke="#333" marker-end="url(#ar)"/>
<rect x="613" y="222" width="110" height="246" fill="none" stroke="#38761d" stroke-dasharray="3,3"/>
<text x="668" y="232" text-anchor="middle" font-weight="bold" font-size="8.5">módulo pedidos</text><text x="668" y="240" text-anchor="middle" font-size="6.5" fill="#555">src/modules/pedidos/</text>
<rect x="625" y="246" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="668" y="258" text-anchor="middle" font-size="7.5">pedidos.routes.js</text>
<line x1="668" y1="265" x2="668" y2="278" stroke="#333" marker-end="url(#ar)"/>
<rect x="625" y="279" width="86" height="19" fill="#fff" stroke="#3b5b9d"/><text x="668" y="291" text-anchor="middle" font-size="7.5">pedidos.controller.js</text>
<line x1="668" y1="298" x2="668" y2="338" stroke="#333" marker-end="url(#ar)"/>
<rect x="625" y="340" width="86" height="30" fill="#d3e5c8" stroke="#38761d"/><text x="668" y="353" text-anchor="middle" font-weight="bold" font-size="7.5">pedidos.service.js</text><text x="668" y="363" text-anchor="middle" font-size="6.5">checkout, estados, pago/envío</text>
<line x1="668" y1="370" x2="668" y2="428" stroke="#333" marker-end="url(#ar)"/>
<rect x="625" y="430" width="86" height="20" fill="#fff" stroke="#bf9000"/><text x="668" y="443" text-anchor="middle" font-size="7.5">pedidos.repository.js</text>
<line x1="668" y1="450" x2="668" y2="476" stroke="#333" marker-end="url(#ar)"/>
<line x1="372" y1="355" x2="360" y2="355" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/>
<line x1="493" y1="355" x2="482" y2="355" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/>
<line x1="625" y1="355" x2="603" y2="355" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/>
<line x1="250" y1="355" x2="238" y2="355" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/>
<path d="M668,372 L668,396 L208,396 L208,372" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/>
<rect x="124" y="478" width="604" height="26" fill="#fde4bb" stroke="#bf9000"/><text x="426" y="494" text-anchor="middle" font-size="8"><tspan font-weight="bold">Acceso a datos compartido</tspan>  Sequelize (ORM) · modelos · pool de conexiones <tspan fill="#8a6d00">(src/shared/db)</tspan></text>
<line x1="427" y1="504" x2="427" y2="556" stroke="#333" marker-end="url(#ar)"/><text x="433" y="542" font-size="7.5" fill="#333">SQL · TCP 5432</text>
<rect x="380" y="557" width="94" height="54" fill="#fff" stroke="#333"/><text x="427" y="583" text-anchor="middle" font-weight="bold" font-size="9">PostgreSQL</text><text x="427" y="595" text-anchor="middle" font-size="8">marketplace_db</text>
<rect x="781" y="273" width="114" height="44" fill="#eeeeee" stroke="#666"/><text x="838" y="288" text-anchor="middle" font-size="6.5" fill="#555">«sistema externo»</text><text x="838" y="298" text-anchor="middle" font-weight="bold" font-size="8">Pasarela de pagos</text><text x="838" y="308" text-anchor="middle" font-size="6.5">(p. ej. Culqi / Niubiz)</text>
<rect x="781" y="388" width="114" height="44" fill="#eeeeee" stroke="#666"/><text x="838" y="403" text-anchor="middle" font-size="6.5" fill="#555">«sistema externo»</text><text x="838" y="413" text-anchor="middle" font-weight="bold" font-size="8">Servicio de envíos</text><text x="838" y="423" text-anchor="middle" font-size="6.5">(API del courier)</text>
<path d="M716,346 L765,346 L765,295 L779,295" fill="none" stroke="#333" marker-end="url(#ar)"/><text x="743" y="341" text-anchor="middle" font-size="7">HTTPS / REST</text>
<path d="M716,362 L765,362 L765,410 L779,410" fill="none" stroke="#333" marker-end="url(#ar)"/><text x="743" y="376" text-anchor="middle" font-size="7">HTTPS / REST</text>
<rect x="14" y="548" width="358" height="94" fill="#fff" stroke="#999"/><text x="22" y="563" font-weight="bold" font-size="8">Leyenda</text>
<line x1="26" y1="575" x2="58" y2="575" stroke="#333" marker-end="url(#ar)"/><text x="68" y="578" font-size="7">Llamada síncrona entre capas (de arriba hacia abajo)</text>
<line x1="26" y1="590" x2="58" y2="590" stroke="#38761d" stroke-dasharray="4,3" fill="none" marker-end="url(#ag)"/><text x="68" y="593" font-size="7">Uso entre módulos (solo a través de su service)</text>
<rect x="26" y="601" width="32" height="10" fill="none" stroke="#38761d" stroke-dasharray="3,3"/><text x="68" y="609" font-size="7">Límite de módulo (carpeta src/modules/&lt;módulo&gt;)</text>
<rect x="26" y="619" width="32" height="10" fill="#eee" stroke="#666"/><text x="68" y="627" font-size="7">Sistema externo (fuera del monolito)</text>
<rect x="494" y="548" width="254" height="94" fill="#fff" stroke="#999"/><text x="502" y="563" font-weight="bold" font-size="8">Reglas de la arquitectura</text>
<text x="502" y="577" font-size="7">1. Cada capa solo invoca a la capa inmediatamente inferior.</text>
<text x="502" y="589" font-size="7">2. Un módulo no accede al repository ni a las tablas de otro módulo.</text>
<text x="502" y="601" font-size="7">3. La comunicación entre módulos se hace llamando a su service.</text>
<text x="502" y="613" font-size="7">4. Todo se ejecuta en un único proceso Node.js con una única BD.</text>
</svg>




# Estilo arquitectónico

**Estilo seleccionado:** Monolito modular con arquitectura en capas.

Todo el backend se ejecuta como una sola aplicación (un solo proceso y un solo despliegue), organizada en módulos independientes y en tres capas: presentación, lógica de negocio y datos. Esta decisión responde a los drivers DA01 (Escalabilidad) y DA06 (Mantenibilidad), y está registrada en ADR-001.





## Reglas de la arquitectura

1. Cada capa solo invoca a la capa inmediatamente inferior.
2. Un módulo no accede al repository ni a las tablas de otro módulo.
3. La comunicación entre módulos se hace llamando a su service.
4. Todo se ejecuta en un único proceso Node.js con una única base de datos.