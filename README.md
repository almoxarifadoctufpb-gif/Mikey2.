

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
  <meta name="theme-color" content="#0A0A0F">
  <title>Almox CT UFPB</title>
  <link rel="manifest" href="manifest.json">
  <link rel="apple-touch-icon" href="Gemini_Generated_Image_hh2cyjhh2cyjhh2c.png">
  <link rel="icon" type="image/png" href="Logo Inicial do APP.jpeg">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.28/jspdf.plugin.autotable.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/html5-qrcode/minified/html5-qrcode.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/qrcode-generator@1.4.4/qrcode.min.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <style>
    /* ========== RESET & TEMA AZUL INSTITUCIONAL ========== */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', 'Segoe UI', system-ui, -apple-system, sans-serif;
      background: linear-gradient(145deg, #0A2B3E 0%, #05212E 100%);
      color: #EFF3F8;
      -webkit-tap-highlight-color: transparent;
    }

    :root {
      --azul-institucional: #0A4B8C;
      --azul-escuro: #083A6E;
      --azul-claro: #1E5A9E;
      --azul-grad: linear-gradient(135deg, #0A4B8C, #1E3A6F);
      --bg-dark: #0A2B3E;
      --bg-card: rgba(10, 75, 140, 0.12);
      --glass-border: rgba(30, 90, 158, 0.3);
      --glass-blur: blur(12px);
      --accent-primary: #0A4B8C;
      --accent-secondary: #2C7AB1;
      --accent-glow: rgba(10, 75, 140, 0.5);
      --success: #2C9C5A;
      --warning: #E67E22;
      --danger: #C0392B;
      --text-primary: #F0F4F8;
      --text-secondary: #B0C4DE;
      --border-light: rgba(30, 90, 158, 0.25);
      --shadow-md: 0 8px 20px rgba(0, 0, 0, 0.3);
      --shadow-glow: 0 0 15px rgba(10, 75, 140, 0.5);
      --transition: all 0.2s cubic-bezier(0.2, 0.9, 0.4, 1.1);
    }

    ::-webkit-scrollbar { width: 5px; }
    ::-webkit-scrollbar-track { background: #0F2A36; }
    ::-webkit-scrollbar-thumb { background: var(--azul-institucional); border-radius: 20px; }

    /* Splash Screen */
    #splash-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: linear-gradient(145deg, #0A2B3E, #05212E);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      z-index: 9999;
      transition: opacity 0.6s ease;
    }
    #splash-screen img {
      width: 120px;
      height: 120px;
      object-fit: contain;
      border-radius: 36px;
      background: rgba(255,255,255,0.1);
      padding: 12px;
      box-shadow: 0 20px 35px -10px rgba(0,0,0,0.5);
      margin-bottom: 24px;
      border: 1px solid rgba(255,255,255,0.2);
    }
    #splash-screen span {
      font-size: 28px;
      font-weight: 600;
      background: linear-gradient(135deg, #FFF, #A0C4FF);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    /* App container */
    .app-container {
      max-width: 500px;
      margin: 0 auto;
      background: transparent;
      min-height: 100vh;
      position: relative;
    }

    /* Header */
    .header {
      background: rgba(10, 43, 62, 0.85);
      backdrop-filter: blur(16px);
      border-bottom: 1px solid var(--glass-border);
      padding: 18px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 0 0 32px 32px;
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
      position: sticky;
      top: 0;
      z-index: 100;
    }
    .header-logo {
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .header-logo img {
      width: 48px;
      height: 48px;
      border-radius: 20px;
      background: white;
      padding: 6px;
      object-fit: contain;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }
    .header-title h1 {
      font-size: 1.2rem;
      font-weight: 700;
      background: linear-gradient(120deg, #FFF, #7FB3FF);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }
    .header-title p {
      font-size: 0.7rem;
      color: var(--text-secondary);
    }
    .header-icons {
      display: flex;
      gap: 12px;
    }
    .header-icons button {
      background: rgba(255,255,255,0.08);
      border: none;
      width: 44px;
      height: 44px;
      border-radius: 28px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: var(--transition);
      position: relative;
    }
    .header-icons button:hover {
      background: rgba(255,255,255,0.18);
      transform: scale(0.96);
    }
    .cart-badge {
      position: absolute;
      top: -4px;
      right: -4px;
      background: linear-gradient(135deg, #EF4444, #DC2626);
      color: white;
      font-size: 0.65rem;
      font-weight: bold;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      border: 2px solid var(--bg-dark);
    }

    /* Main Content */
    .main-content {
      padding: 20px 16px;
      padding-bottom: 90px;
    }

    /* Anúncios */
    .announcements-container {
      margin-bottom: 24px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .announcement-banner {
      background: rgba(10, 75, 140, 0.2);
      backdrop-filter: blur(8px);
      border-radius: 28px;
      padding: 16px 20px;
      border-left: 5px solid;
      box-shadow: var(--shadow-md);
      transition: var(--transition);
    }
    .announcement-banner:hover { transform: translateY(-2px); }
    .priority-info { border-left-color: var(--azul-institucional); background: rgba(10,75,140,0.2); }
    .priority-warning { border-left-color: var(--warning); background: rgba(230,126,34,0.1); }
    .priority-urgent { border-left-color: var(--danger); background: rgba(192,57,43,0.1); }

    /* Banner download */
    .download-banner {
      background: linear-gradient(145deg, #0F2A36, #0A1F2A);
      border-radius: 32px;
      padding: 16px 20px;
      margin-bottom: 24px;
      display: flex;
      align-items: center;
      gap: 16px;
      cursor: pointer;
      border: 1px solid var(--glass-border);
      transition: var(--transition);
    }
    .download-banner:hover { transform: scale(1.01); background: #0F2A36; }

    /* Catálogo Grid */
    .catalog-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .product-card {
      background: rgba(10, 43, 62, 0.7);
      backdrop-filter: blur(4px);
      border-radius: 32px;
      overflow: hidden;
      border: 1px solid var(--glass-border);
      transition: var(--transition);
      box-shadow: 0 8px 20px rgba(0,0,0,0.2);
    }
    .product-card:hover {
      transform: translateY(-6px);
      border-color: var(--azul-institucional);
      box-shadow: var(--shadow-glow);
    }
    .product-image {
      height: 140px;
      background: linear-gradient(145deg, #0F2A36, #1E3A4A);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
      color: var(--azul-institucional);
    }
    .product-info {
      padding: 16px;
    }
    .product-info h4 {
      font-size: 1rem;
      font-weight: 700;
      margin-bottom: 4px;
    }
    .product-category {
      font-size: 0.7rem;
      color: var(--text-secondary);
      margin-bottom: 6px;
    }
    .product-stock {
      display: flex;
      justify-content: space-between;
      margin: 12px 0;
    }
    .stock-badge {
      padding: 4px 12px;
      border-radius: 30px;
      font-size: 0.7rem;
      font-weight: 600;
      background: rgba(0,0,0,0.3);
    }
    .stock-badge.normal { background: rgba(44,156,90,0.2); color: #2C9C5A; }
    .stock-badge.low { background: rgba(230,126,34,0.2); color: #F39C12; }
    .stock-badge.zero { background: rgba(192,57,43,0.2); color: #E74C3C; }

    /* Botões */
    .btn-cart, .btn-primary, .action-btn.primary {
      background: linear-gradient(95deg, var(--azul-institucional), var(--azul-claro));
      border: none;
      padding: 12px;
      border-radius: 28px;
      font-weight: 600;
      color: white;
      width: 100%;
      transition: var(--transition);
      cursor: pointer;
      font-size: 0.85rem;
    }
    .btn-cart:hover, .btn-primary:hover {
      transform: scale(0.98);
      box-shadow: var(--shadow-glow);
    }
    .btn-secondary {
      background: rgba(255,255,255,0.08);
      border: 1px solid var(--glass-border);
      padding: 12px;
      border-radius: 28px;
      font-weight: 500;
      color: var(--text-primary);
      cursor: pointer;
      transition: var(--transition);
    }
    .btn-danger {
      background: linear-gradient(135deg, #C0392B, #E74C3C);
      border: none;
      color: white;
      border-radius: 28px;
      padding: 10px 20px;
      font-weight: 600;
    }

    /* Filtros */
    .category-filters {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 24px;
    }
    .filter-chip {
      background: rgba(10, 43, 62, 0.7);
      backdrop-filter: blur(4px);
      border-radius: 40px;
      padding: 8px 18px;
      font-size: 0.8rem;
      font-weight: 500;
      cursor: pointer;
      border: 1px solid var(--glass-border);
      transition: var(--transition);
    }
    .filter-chip.active {
      background: linear-gradient(95deg, var(--azul-institucional), var(--azul-claro));
      border-color: transparent;
      color: white;
    }

    /* Carrinho */
    .cart-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      backdrop-filter: blur(8px);
      display: none;
      justify-content: flex-end;
      z-index: 2000;
    }
    .cart-overlay.active {
      display: flex;
    }
    .cart-panel {
      background: #0F2A36;
      width: 100%;
      max-width: 400px;
      height: 100%;
      overflow-y: auto;
      border-left: 1px solid var(--glass-border);
      box-shadow: -10px 0 30px rgba(0,0,0,0.5);
    }
    .cart-header {
      padding: 24px;
      background: rgba(0,0,0,0.4);
      backdrop-filter: blur(12px);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .cart-item {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 16px 0;
      border-bottom: 1px solid var(--glass-border);
    }
    .cart-item-actions button {
      width: 32px;
      height: 32px;
      border-radius: 10px;
      background: rgba(0,0,0,0.3);
      border: 1px solid var(--glass-border);
      color: white;
      cursor: pointer;
    }

    /* Modais */
    .modal-overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      backdrop-filter: blur(12px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 3000;
    }
    .modal-overlay.active {
      display: flex;
    }
    .modal {
      background: rgba(10, 43, 62, 0.95);
      backdrop-filter: blur(20px);
      width: 90%;
      max-width: 450px;
      border-radius: 48px;
      border: 1px solid var(--glass-border);
      overflow: hidden;
      animation: modalUp 0.3s ease;
    }
    @keyframes modalUp {
      from { transform: translateY(30px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }
    .modal-header {
      padding: 24px;
      background: linear-gradient(135deg, #0A2B3E, #0F2A36);
      font-weight: 700;
      font-size: 1.3rem;
    }

    /* Inputs */
    .form-group input, .form-group select, .form-group textarea {
      background: rgba(0,0,0,0.4);
      border: 1px solid var(--glass-border);
      border-radius: 28px;
      padding: 14px 18px;
      width: 100%;
      color: white;
      font-size: 0.9rem;
      transition: var(--transition);
    }
    .form-group input:focus, .form-group select:focus, .form-group textarea:focus {
      border-color: var(--azul-institucional);
      outline: none;
      box-shadow: 0 0 0 2px rgba(10,75,140,0.3);
    }

    /* Bottom Nav */
    .bottom-nav {
      position: fixed;
      bottom: 0;
      max-width: 500px;
      width: 100%;
      background: rgba(10, 43, 62, 0.9);
      backdrop-filter: blur(20px);
      display: flex;
      justify-content: space-around;
      padding: 8px 12px 20px;
      border-top: 1px solid var(--glass-border);
      border-radius: 32px 32px 0 0;
      z-index: 100;
    }
    .nav-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      background: none;
      border: none;
      color: var(--text-secondary);
      font-size: 0.7rem;
      font-weight: 500;
      padding: 6px 12px;
      border-radius: 40px;
      transition: var(--transition);
      cursor: pointer;
    }
    .nav-item.active {
      color: white;
      background: rgba(10,75,140,0.3);
      transform: translateY(-2px);
    }
    .nav-item span:first-child {
      font-size: 1.2rem;
    }

    /* WhatsApp float */
    .whatsapp-float {
      position: fixed;
      bottom: 90px;
      right: 20px;
      width: 56px;
      height: 56px;
      background: #25D366;
      border-radius: 30px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 8px 20px rgba(0,0,0,0.3);
      cursor: pointer;
      z-index: 1000;
      transition: var(--transition);
    }
    .whatsapp-float:active { transform: scale(0.9); }

    /* Toast */
    .toast-notification {
      position: fixed;
      bottom: 100px;
      left: 50%;
      transform: translateX(-50%);
      background: #0F2A36;
      backdrop-filter: blur(16px);
      padding: 12px 24px;
      border-radius: 60px;
      color: white;
      font-weight: 500;
      z-index: 4000;
      opacity: 0;
      transition: opacity 0.2s;
      pointer-events: none;
      border: 1px solid var(--glass-border);
    }
    .toast-notification.show {
      opacity: 1;
    }

    /* Cards de gestão */
    .tracking-container, .water-stock-control, .dashboard-cards {
      background: rgba(10, 43, 62, 0.6);
      backdrop-filter: blur(8px);
      border-radius: 32px;
      padding: 20px;
      margin-bottom: 20px;
    }
    .item-card {
      background: rgba(0,0,0,0.3);
      border-radius: 28px;
      padding: 16px;
      margin-bottom: 12px;
    }
    @media (max-width: 450px) {
      .catalog-grid { grid-template-columns: 1fr; }
    }

    /* Status */
    .status-pendente, .status-aguardando { background: rgba(230,126,34,0.2); color: #F39C12; }
    .status-aprovado, .status-confirmado { background: rgba(44,156,90,0.2); color: #2C9C5A; }
    .status-entregue { background: rgba(10,75,140,0.2); color: #5DADE2; }
    .status-negado { background: rgba(192,57,43,0.2); color: #E74C3C; }
    .status-analise { background: rgba(52,152,219,0.2); color: #3498db; }

    /* QR items */
    .qr-item-card {
      display: flex;
      align-items: center;
      gap: 12px;
      background: rgba(0,0,0,0.3);
      border-radius: 28px;
      padding: 12px;
      margin-bottom: 12px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div id="splash-screen">
    <img src="Logo almoxarifado.png" alt="Almox CT UFPB" id="splash-logo">
    <span>Almox CT UFPB</span>
  </div>
  <div class="app-container" id="app-container" style="display: none;">
    <div class="header">
      <div class="header-logo">
        <img src="Foto de página inicial.jpeg" alt="Logo" id="header-logo">
        <div class="header-title">
          <h1>Almox CT UFPB</h1>
          <p id="user-greeting">Almoxarifado</p>
        </div>
      </div>
      <div class="header-icons">
        <button id="cart-button" onclick="app.openCart()" title="Carrinho">
          <span style="font-size:1.5rem;">🛒</span>
          <span id="cart-count" class="cart-badge" style="display: none;">0</span>
        </button>
        <button id="download-pdf-btn" onclick="app.baixarPDFRecente()" title="Baixar PDF">
          <span style="font-size:1.5rem;">📄</span>
        </button>
        <button id="admin-login-btn" class="admin-login-btn" onclick="app.toggleAdmin()">
          <span style="font-size:1.5rem;">👤</span>
        </button>
      </div>
    </div>
    <div class="main-content" id="main-content"></div>
    <nav class="bottom-nav" id="bottom-nav"></nav>
  </div>

  <!-- Modais com IDs corrigidos -->
  <div class="cart-overlay" id="cart-overlay"><div class="cart-panel"><div class="cart-header"><h2>🛒 Carrinho</h2><button onclick="app.closeCart()">×</button></div><div class="cart-items" id="cart-items"></div><div class="cart-total" id="cart-total"><span>Total de itens:</span><span id="total-items">0</span></div><div class="cart-footer"><button class="btn-secondary" onclick="app.clearCart()">Limpar</button><button class="btn-primary" onclick="app.openCheckoutModal()">Finalizar</button></div></div></div>
  <div class="modal-overlay" id="modal-produto"><div class="modal"><div class="modal-header" id="modal-produto-title">➕ Novo Produto</div><div class="modal-body"><form id="form-produto" onsubmit="event.preventDefault(); app.salvarProduto();"><input type="hidden" id="produto-id"><div class="form-group"><label>Nome *</label><input type="text" id="produto-nome" required></div><div class="form-group"><label>Categoria</label><select id="produto-categoria"></select></div><div class="form-group"><label>Descrição</label><textarea id="produto-descricao" rows="2"></textarea></div><div class="form-group"><label>Unidade *</label><input type="text" id="produto-unidade" required value="un"></div><div class="form-group"><label>Estoque *</label><input type="number" id="produto-estoque" required min="0" value="0"></div><div class="form-group"><label>Estoque Mínimo</label><input type="number" id="produto-minstock" min="0" value="5"></div><div class="form-group"><label>Localização</label><input type="text" id="produto-localizacao"></div><div class="form-group"><label>Valor Unitário (R$)</label><input type="number" id="produto-valor" step="0.01" min="0" value="0.00"></div><div class="form-group"><label>Foto</label><input type="file" id="produto-foto" accept="image/*" onchange="app.previewImage(event)"><div id="image-preview" class="image-preview"><span>Pré-visualização</span></div></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-produto')">Cancelar</button><button class="btn-primary" onclick="app.salvarProduto()">Salvar</button></div></div></div>
  <div class="modal-overlay" id="modal-aviso"><div class="modal"><div class="modal-header" id="modal-aviso-title">📢 Aviso</div><div class="modal-body"><form id="form-aviso"><input type="hidden" id="aviso-id"><div class="form-group"><label>Título *</label><input type="text" id="aviso-titulo" required></div><div class="form-group"><label>Mensagem *</label><textarea id="aviso-mensagem" rows="3" required></textarea></div><div class="form-group"><label>Data início</label><input type="date" id="aviso-inicio"></div><div class="form-group"><label>Data término</label><input type="date" id="aviso-termino"></div><div class="form-group"><label>Prioridade *</label><select id="aviso-prioridade" required><option value="info">📘 Informativo</option><option value="warning">⚠️ Atenção</option><option value="urgent">🚨 Urgente</option></select></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-aviso')">Cancelar</button><button class="btn-primary" onclick="app.salvarAviso()">Salvar</button></div></div></div>
  <div class="modal-overlay" id="modal-checkout"><div class="modal"><div class="modal-header">📦 Finalizar Pedido</div><div class="modal-body"><form id="form-pedido"><div class="form-group"><label>Nome *</label><input type="text" id="pedido-nome" required></div><div class="form-group"><label>E-mail *</label><input type="email" id="pedido-email" required></div><div class="form-group" id="pedido-setor-group"></div><div class="form-group" id="outro-setor-group" style="display:none;"><label>Digite o setor</label><input type="text" id="pedido-setor-outro"></div><div class="form-group"><label>Observações</label><textarea id="pedido-obs" rows="2"></textarea></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-checkout')">Cancelar</button><button class="btn-primary" onclick="app.finalizarPedido()">Solicitar</button></div></div></div>
  <div class="modal-overlay" id="modal-admin-login"><div class="modal"><div class="modal-header">🔒 Acesso</div><div class="modal-body"><div class="form-group"><label>Login</label><input type="text" id="admin-email" value="almoxarifadoCT"></div><div class="form-group"><label>Senha</label><input type="password" id="admin-password"></div></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-admin-login')">Cancelar</button><button class="btn-primary" onclick="app.adminLogin()">Entrar</button></div></div></div>
  <div class="modal-overlay" id="modal-usuarios"><div class="modal"><div class="modal-header">👥 Permissões</div><div class="modal-body" id="usuarios-body"></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-usuarios')">Fechar</button></div></div></div>
  <div class="modal-overlay" id="modal-pedido-realizado"><div class="modal"><div class="modal-header">✅ Pedido Realizado</div><div class="modal-body" style="text-align:center;"><p>Solicitação registrada!</p><p><strong>Código:</strong></p><p id="tracking-code-display" style="font-size:2rem; font-weight:700; background:rgba(0,0,0,0.4); padding:15px; border-radius:30px;">AGUA-123ABC</p><div><button class="btn-primary" onclick="app.baixarPDFRecente()">Baixar PDF</button><button class="btn-secondary" onclick="app.enviarPDFEmail()">📧 Enviar</button></div></div><div class="modal-footer"><button class="btn-primary" onclick="app.closeModal('modal-pedido-realizado')">OK</button></div></div></div>
  <div class="modal-overlay" id="modal-detalhes-agua"><div class="modal"><div class="modal-header">📋 Detalhes</div><div class="modal-body" id="detalhes-agua-body"></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-detalhes-agua')">Fechar</button></div></div></div>
  <div class="modal-overlay" id="modal-manifestacao"><div class="modal"><div class="modal-header">📢 Manifestação</div><div class="modal-body"><form id="form-manifestacao"><div class="form-group"><label>Tipo *</label><select id="manifestacao-tipo" required onchange="app.sugerirCategoriaManifestacao()"><option value="">Selecione</option><option value="reclamacao">Reclamação</option><option value="sugestao">Sugestão</option><option value="elogio">Elogio</option><option value="duvida">Dúvida</option><option value="denuncia">Denúncia</option></select></div><div class="form-group"><label>Categoria</label><select id="manifestacao-categoria"><option value="">Automática</option><option value="falta_material">Falta de material</option><option value="atraso_entrega">Atraso</option><option value="problema_sistema">Sistema</option><option value="atendimento">Atendimento</option><option value="outros">Outros</option></select></div><div class="form-group"><label>Descrição *</label><textarea id="manifestacao-descricao" rows="4" required onkeyup="app.sugerirFAQ(this.value)"></textarea><div id="faq-sugestoes"></div></div><div class="form-group"><label>Anexo</label><input type="file" id="manifestacao-anexo"></div><div class="form-group"><label><input type="checkbox" id="manifestacao-anonimo" onchange="app.toggleIdentificacao()"> Anônimo</label></div><div id="manifestacao-identificacao"><div class="form-group"><label>Nome</label><input type="text" id="manifestacao-nome"></div><div class="form-group"><label>E-mail</label><input type="email" id="manifestacao-email"></div></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-manifestacao')">Cancelar</button><button class="btn-primary" onclick="app.registrarManifestacao()">Enviar</button></div></div></div>
  <div class="modal-overlay" id="modal-acompanhar-manifestacao"><div class="modal"><div class="modal-header">📬 Acompanhar</div><div class="modal-body" id="acompanhar-manifestacao-body"></div><div class="modal-footer" id="acompanhar-manifestacao-footer"><button class="btn-secondary" onclick="app.closeModal('modal-acompanhar-manifestacao')">Fechar</button></div></div></div>
  <div class="modal-overlay" id="modal-avaliar-manifestacao"><div class="modal"><div class="modal-header">⭐ Avaliação</div><div class="modal-body"><p>Avalie o atendimento</p><div class="rating-stars" id="rating-stars"><span data-value="1">★</span><span data-value="2">★</span><span data-value="3">★</span><span data-value="4">★</span><span data-value="5">★</span></div><div class="form-group"><label>Comentário</label><textarea id="avaliacao-comentario" rows="3"></textarea></div></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-avaliar-manifestacao')">Agora não</button><button class="btn-primary" onclick="app.avaliarManifestacao()">Enviar</button></div></div></div>
  <div class="modal-overlay" id="modal-qr-item"><div class="modal"><div class="modal-header" id="modal-qr-item-title">📱 Item QR</div><div class="modal-body"><form id="form-qr-item"><input type="hidden" id="qr-item-id"><div class="form-group"><label>Código</label><input type="text" id="qr-item-code" readonly></div><div class="form-group"><label>Nome *</label><input type="text" id="qr-item-name" required></div><div class="form-group"><label>Categoria *</label><select id="qr-item-category" required onchange="app.sugerirCodigoQR()"><option value="">Selecione</option><option value="MAT">MAT</option><option value="PER">PER</option><option value="LIM">LIM</option><option value="AGUA">AGUA</option><option value="OUT">OUT</option></select></div><div class="form-group"><label>Unidade *</label><input type="text" id="qr-item-unit" required></div><div class="form-group"><label>Localização *</label><input type="text" id="qr-item-location" required></div><div class="form-group"><label>Quantidade *</label><input type="number" id="qr-item-qty" required min="0" value="0"></div><div class="form-group"><label>Estoque Mínimo *</label><input type="number" id="qr-item-minstock" required min="0" value="5"></div><div id="qr-code-preview-group" style="display:none;"><label>QR Code</label><div id="qr-code-preview"></div></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-qr-item')">Cancelar</button><button class="btn-primary" onclick="app.salvarQRItem()">Salvar</button></div></div></div>
  <div class="modal-overlay" id="modal-qr-scanner"><div class="modal"><div class="modal-header">Escanear QR</div><div class="modal-body"><div id="qr-reader" style="width:100%"></div></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeQRScanner()">Fechar</button></div></div></div>
  <div class="modal-overlay" id="modal-qr-entry"><div class="modal"><div class="modal-header">➕ Entrada</div><div class="modal-body"><form id="form-qr-entry"><input type="hidden" id="entry-item-id"><div class="form-group"><label>Item</label><p id="entry-item-name"></p></div><div class="form-group"><label>Quantidade *</label><input type="number" id="entry-qty" required min="1"></div><div class="form-group"><label>Data</label><input type="date" id="entry-date" required></div><div class="form-group"><label>Fornecedor</label><input type="text" id="entry-supplier"></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-qr-entry')">Cancelar</button><button class="btn-primary" onclick="app.confirmarEntrada()">Confirmar</button></div></div></div>
  <div class="modal-overlay" id="modal-qr-exit"><div class="modal"><div class="modal-header">➖ Saída</div><div class="modal-body"><form id="form-qr-exit"><input type="hidden" id="exit-item-id"><div class="form-group"><label>Item</label><p id="exit-item-name"></p></div><div class="form-group"><label>Quantidade *</label><input type="number" id="exit-qty" required min="1"></div><div class="form-group"><label>Data</label><input type="date" id="exit-date" required></div><div class="form-group"><label>Setor</label><input type="text" id="exit-sector"></div></form></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-qr-exit')">Cancelar</button><button class="btn-primary" onclick="app.confirmarSaida()">Confirmar</button></div></div></div>
  <div class="modal-overlay" id="modal-whatsapp-menu"><div class="modal"><div class="modal-header">💬 WhatsApp</div><div class="modal-body"><div class="form-group"><label>Assunto</label><select id="whatsapp-assunto" onchange="app.atualizarMensagemWhatsApp()"><option value="duvidas">Dúvidas</option><option value="problema">Problema</option><option value="solicitacao">Solicitação</option><option value="outros">Outros</option></select></div><div class="form-group"><label>Mensagem</label><textarea id="whatsapp-mensagem" rows="5" readonly></textarea></div></div><div class="modal-footer"><button class="btn-secondary" onclick="app.closeModal('modal-whatsapp-menu')">Cancelar</button><button class="btn-primary" onclick="app.abrirWhatsApp()">Abrir</button></div></div></div>
  <div id="toast-notification" class="toast-notification">Item adicionado</div>
  <button class="whatsapp-float" id="whatsapp-float-btn"><span style="font-size:1.8rem;">💬</span></button>

  <script>
    // ===================== CÓDIGO CORRIGIDO =====================
    const SETORES_API_URL = 'https://script.google.com/macros/s/AKfycbxnRM0SdHjnnvMAbOufVXMuZb5ECTXTR8XLVsxgpMRImWsXTeZksJ7Igen3RmSwcvymuw/exec';
    const API_URL = 'https://script.google.com/macros/s/AKfycbxYMg6hOGvqBF00zDNb22KVPj6wZ3QgmYJXj3ev0tO9orWBAgaTFRui54lOrzGZBQXO0A/exec';

    async function buscarSetores() {
      try {
        const resposta = await fetch(SETORES_API_URL + '?action=setores');
        if (!resposta.ok) throw new Error(`HTTP ${resposta.status}`);
        const setores = await resposta.json();
        return Array.isArray(setores) ? setores : [];
      } catch (error) {
        console.error("Erro ao buscar setores:", error);
        return ['Administração', 'Laboratório 1', 'Laboratório 2', 'Secretaria', 'Outro'];
      }
    }

    const TIPOS_MANIFESTACAO = { reclamacao: 'Reclamação', sugestao: 'Sugestão', elogio: 'Elogio', duvida: 'Dúvida', denuncia: 'Denúncia' };
    const STATUS_MANIFESTACAO = { recebido: 'Recebido', analise: 'Em análise', atendimento: 'Em atendimento', concluido: 'Concluído' };

    const app = {
      currentUser: null,
      isAdmin: false,
      isEntregador: false,
      db: {
        users: [], products: [], requests: [], waterRequests: [], movements: [],
        categories: ['Papelaria', 'Informática', 'Limpeza', 'Materiais de escritório', 'Higiene', 'Manutenção'],
        announcements: [], waterStockMovements: [], complaints: [], complaintMessages: [],
        qrItems: [], qrTransactions: [], whatsappLogs: []
      },
      cart: [],
      recentPDF: null,
      grafico: null,
      currentComplaintId: null,
      html5QrCode: null,

      init: async function() {
        try {
          this.loadDatabase();
          this.hideSplash();
          this.setupEventListeners();
          this.loadCart();
          this.populateCategorySelect();
          const savedUser = sessionStorage.getItem('adminUser');
          if (savedUser) {
            this.currentUser = JSON.parse(savedUser);
            this.isAdmin = this.currentUser.role === 'admin';
            this.isEntregador = this.currentUser.role === 'entregador';
            document.getElementById('user-greeting').innerText = `${this.currentUser.role.toUpperCase()}: ${this.currentUser.name}`;
            if(this.isAdmin) {
              this.renderAdminPanel();
              this.renderBottomNav('admin');
            } else if(this.isEntregador) {
              this.abrirGerenciarSolicitacoesAgua();
              this.renderBottomNav('entregas');
            } else {
              this.renderCatalog();
              this.renderBottomNav('catalog');
            }
          } else {
            document.getElementById('user-greeting').innerText = 'Solicitar Água Mineral';
            this.renderCatalog();
            this.renderBottomNav('catalog');
          }
          this.updateCartCount();
          this.updateAdminButtonIcon();
          this.carregarEAtualizar();
          document.getElementById('whatsapp-float-btn').onclick = () => this.abrirMenuWhatsApp();
          setInterval(() => {
            if (document.querySelector('[data-screen="fila"]')) {
              app.renderFilaPublica();
            }
          }, 5000);
        } catch (error) {
          console.error('Erro na inicialização:', error);
          alert('Ocorreu um erro ao carregar o aplicativo.');
        }
      },

      hideSplash: function() {
        setTimeout(() => {
          document.getElementById('splash-screen').style.opacity = '0';
          setTimeout(() => {
            document.getElementById('splash-screen').style.display = 'none';
            document.getElementById('app-container').style.display = 'block';
          }, 500);
        }, 2000);
      },

      loadDatabase: function() {
        const saved = localStorage.getItem('almoxFacilDB');
        if (saved) {
          this.db = JSON.parse(saved);
          if (!Array.isArray(this.db.products)) this.db.products = [];
          if (!Array.isArray(this.db.requests)) this.db.requests = [];
          if (!Array.isArray(this.db.waterRequests)) this.db.waterRequests = [];
          if (!Array.isArray(this.db.users)) this.db.users = [];
          if (!Array.isArray(this.db.movements)) this.db.movements = [];
          if (!Array.isArray(this.db.announcements)) this.db.announcements = [];
          if (!Array.isArray(this.db.waterStockMovements)) this.db.waterStockMovements = [];
          if (!Array.isArray(this.db.complaints)) this.db.complaints = [];
          if (!Array.isArray(this.db.complaintMessages)) this.db.complaintMessages = [];
          if (!Array.isArray(this.db.qrItems)) this.db.qrItems = [];
          if (!Array.isArray(this.db.qrTransactions)) this.db.qrTransactions = [];
          if (!Array.isArray(this.db.whatsappLogs)) this.db.whatsappLogs = [];
          this.db.products.forEach(p => {
            if (!p.description) p.description = 'Sem descrição';
            if (!p.unit) p.unit = 'un';
            if (!p.imageEmoji && !p.imageBase64) p.imageEmoji = '🖼';
            if (!p.minStock) p.minStock = 5;
            if (!p.location) p.location = '';
            if (!p.unitValue) p.unitValue = 0;
          });
        } else {
          this.initializeDefaultData();
        }
        const aguaExists = this.db.products.some(p => p.name.includes('Água') || p.category === 'Água mineral');
        if (!aguaExists) {
          this.db.products.push({ id: Date.now(), name: 'Água Mineral', description: 'Garrafão 20L', category: 'Água mineral', unit: 'garrafão', stock: 30, minStock: 5, location: 'C1', unitValue: 12.00, imageEmoji: '💧', imageBase64: null });
        }
        const masterExists = this.db.users.find(u => u.email === 'almoxarifadoCT');
        if (!masterExists) {
          this.db.users.push({ id: 1, name: 'Administrador Geral', email: 'almoxarifadoCT', password: btoa('almoxarifado1989'), siape: '00000', sector: 'Almoxarifado', role: 'admin' });
        } else {
          const master = this.db.users.find(u => u.email === 'almoxarifadoCT');
          if (master && master.password !== btoa('almoxarifado1989')) {
            master.password = btoa('almoxarifado1989');
          }
        }
        this.saveDatabase();
      },

      initializeDefaultData: function() {
        this.db.users = [
          {id: 1, name: 'Administrador Geral', email: 'almoxarifadoCT', password: btoa('almoxarifado1989'), siape: '1234567', sector: 'Almoxarifado', role: 'admin'},
          {id: 2, name: 'João Entregador', email: 'entregador', password: btoa('123'), siape: '7654321', sector: 'Logística', role: 'entregador'},
          {id: 3, name: 'Maria Solicitante', email: 'solicitante', password: btoa('123'), siape: '1111111', sector: 'DCOMP', role: 'solicitante'}
        ];
        this.db.products = [
          {id: 1, name: 'Papel A4', description: 'Resma 500 folhas', category: 'Papelaria', unit: 'resma', stock: 50, minStock: 10, location: 'A1', unitValue: 22.50, imageEmoji: '📄', imageBase64: null},
          {id: 2, name: 'Caneta Azul', description: 'Esferográfica', category: 'Papelaria', unit: 'cx', stock: 100, minStock: 20, location: 'A2', unitValue: 1.75, imageEmoji: '✒️', imageBase64: null},
          {id: 3, name: 'Detergente', description: '500ml', category: 'Limpeza', unit: 'un', stock: 5, minStock: 10, location: 'B1', unitValue: 3.20, imageEmoji: '🧴', imageBase64: null},
          {id: 4, name: 'Água Mineral', description: 'Garrafão 20L', category: 'Água mineral', unit: 'garrafão', stock: 30, minStock: 5, location: 'C1', unitValue: 12.00, imageEmoji: '💧', imageBase64: null},
          {id: 5, name: 'Mouse Óptico', description: 'USB', category: 'Informática', unit: 'un', stock: 8, minStock: 3, location: 'D2', unitValue: 25.90, imageEmoji: '🖱️', imageBase64: null},
          {id: 6, name: 'Pasta Arquivo', description: 'Polionda', category: 'Materiais de escritório', unit: 'un', stock: 40, minStock: 10, location: 'A3', unitValue: 5.75, imageEmoji: '📁', imageBase64: null},
          {id: 7, name: 'Clips', description: 'Caixa 100 un', category: 'Papelaria', unit: 'cx', stock: 15, minStock: 5, location: 'A4', unitValue: 3.50, imageEmoji: '📎', imageBase64: null},
          {id: 8, name: 'Sabonete Líquido', description: 'Refil 5L', category: 'Higiene', unit: 'refil', stock: 12, minStock: 4, location: 'B2', unitValue: 18.90, imageEmoji: '🧼', imageBase64: null},
          {id: 9, name: 'Papel Toalha', description: 'Pacote 2 rolos', category: 'Higiene', unit: 'pacote', stock: 20, minStock: 6, location: 'B3', unitValue: 8.40, imageEmoji: '🧻', imageBase64: null},
          {id: 10, name: 'Teclado USB', description: 'ABNT2', category: 'Informática', unit: 'un', stock: 5, minStock: 2, location: 'D1', unitValue: 42.00, imageEmoji: '⌨️', imageBase64: null}
        ];
        this.db.requests = [];
        this.db.waterRequests = [];
        this.db.movements = [];
        this.db.announcements = [];
        this.db.waterStockMovements = [];
        this.db.complaints = [];
        this.db.complaintMessages = [];
        this.db.qrItems = [];
        this.db.qrTransactions = [];
        this.db.whatsappLogs = [];
        this.saveDatabase();
      },

      saveDatabase: function() {
        try {
          localStorage.setItem('almoxFacilDB', JSON.stringify(this.db));
        } catch (error) {
          console.error('Erro ao salvar localStorage:', error);
        }
      },

      consultarPosicaoFila: async function(codigo) {
        try {
          const response = await fetch(`${API_URL}?action=queue&codigo=${encodeURIComponent(codigo)}`);
          return await response.json();
        } catch (error) {
          return { success: false, error: error.toString() };
        }
      },

      abrirMenuWhatsApp: function() { this.atualizarMensagemWhatsApp(); this.openModal('modal-whatsapp-menu'); },
      atualizarMensagemWhatsApp: function() { const assunto = document.getElementById('whatsapp-assunto').value; let msg = ''; const nome = this.currentUser?.name || ''; const base = 'Olá, estou entrando em contato pelo aplicativo do almoxarifado.'; if(assunto==='duvidas') msg = `${base} Gostaria de tirar dúvidas.`; else if(assunto==='problema') msg = `${base} Estou com um problema.`; else msg = `${base} Preciso de suporte.`; document.getElementById('whatsapp-mensagem').value = msg; },
      abrirWhatsApp: function() { const mensagem = document.getElementById('whatsapp-mensagem').value; const numero = '558332167082'; const url = /iPhone|iPad|iPod|Android/i.test(navigator.userAgent) ? `https://wa.me/${numero}?text=${encodeURIComponent(mensagem)}` : `https://web.whatsapp.com/send?phone=${numero}&text=${encodeURIComponent(mensagem)}`; this.db.whatsappLogs.push({ data: new Date().toISOString(), usuario: this.currentUser?.name || 'Visitante', mensagem }); this.saveDatabase(); window.open(url, '_blank'); this.closeModal('modal-whatsapp-menu'); this.showNotification('Abrindo WhatsApp...'); },

      populateCategorySelect: function() { const select = document.getElementById('produto-categoria'); if(select) { select.innerHTML = '<option value="">Selecione</option>'; this.db.categories.forEach(cat => { select.innerHTML += `<option value="${cat}">${cat}</option>`; }); } },
      previewImage: function(event) { const file = event.target.files[0]; if(file) { const reader = new FileReader(); reader.onload = function(e) { const preview = document.getElementById('image-preview'); preview.style.backgroundImage = `url('${e.target.result}')`; preview.style.backgroundSize = 'cover'; preview.innerHTML = '<span>Foto selecionada</span>'; preview.classList.add('has-image'); }; reader.readAsDataURL(file); } },
      salvarDados: async function(tipo, dados) { try { const response = await fetch(API_URL, { method: "POST", body: JSON.stringify({ ...dados, tipo: tipo === 'pedidosMateriais' ? 'material' : (tipo === 'pedidosAgua' ? 'agua' : tipo), data: new Date().toISOString() }), headers: { "Content-Type": "application/json" } }); return await response.json(); } catch(e) { return { error: true, message: e.toString() }; } },
      buscarDados: async function(tipo) { try { const response = await fetch(`${API_URL}?action=${tipo === 'setores' ? 'setores' : 'pedidos'}`); return await response.json(); } catch(e) { return { error: true, data: [] }; } },
      salvarAgua: async function(quantidade, usuario) { return this.salvarDados('pedidosAgua', { id: Date.now(), produto: "Água Mineral", quantidade, usuario, data: new Date().toISOString() }); },
      atualizarGraficoAgua: function(qtd) { const canvas = document.getElementById('graficoAgua'); if(!canvas) return; const ctx = canvas.getContext('2d'); if(this.grafico) this.grafico.destroy(); this.grafico = new Chart(ctx, { type: 'bar', data: { labels: ['Água Mineral'], datasets: [{ label: 'Quantidade', data: [qtd], backgroundColor: '#0A4B8C', borderRadius: 8 }] }, options: { responsive: true, maintainAspectRatio: false, scales: { y: { beginAtZero: true } } } }); },
      carregarEAtualizar: async function() { const aguaProduct = this.db.products.find(p => p.name === 'Água Mineral' || p.category === 'Água mineral'); if(aguaProduct) this.atualizarGraficoAgua(aguaProduct.stock); },
      renderSetorDropdown: async function(selectId, outroGroupId, outroInputId, required = true) { const setores = await buscarSetores(); return `<select id="${selectId}" class="setor-select" ${required ? 'required' : ''} onchange="app.toggleOutroSetor('${selectId}', '${outroGroupId}', '${outroInputId}')"><option value="">Selecione</option>${setores.map(s => `<option value="${s}">${s}</option>`).join('')}<option value="OUTRO">Outro</option></select>`; },
      toggleOutroSetor: function(selectId, outroGroupId, outroInputId) { const select = document.getElementById(selectId); const outroGroup = document.getElementById(outroGroupId); if(select.value === 'OUTRO') { outroGroup.style.display = 'block'; document.getElementById(outroInputId).setAttribute('required', 'required'); } else { outroGroup.style.display = 'none'; document.getElementById(outroInputId).removeAttribute('required'); } },
      getSetorValue: function(selectId, outroInputId) { const select = document.getElementById(selectId); return select.value === 'OUTRO' ? document.getElementById(outroInputId).value.trim() : select.value; },
      getActiveAnnouncements: function() { 
        const today = new Date().toISOString().split('T')[0];
        const active = this.db.announcements.filter(a => (!a.startDate || a.startDate <= today) && (!a.endDate || a.endDate >= today));
        // Ordenar por prioridade: urgent (3) > warning (2) > info (1)
        return active.sort((a,b) => {
          const order = { urgent: 3, warning: 2, info: 1 };
          return (order[b.priority] || 0) - (order[a.priority] || 0);
        });
      },
      renderActiveAnnouncements: function() { 
        const active = this.getActiveAnnouncements(); 
        if(active.length===0) return ''; 
        let html = '<div class="announcements-container">'; 
        active.forEach(a => { 
          let priorityClass = 'priority-info', priorityLabel = 'Informativo'; 
          if(a.priority === 'warning') { priorityClass = 'priority-warning'; priorityLabel = 'Atenção'; } 
          else if(a.priority === 'urgent') { priorityClass = 'priority-urgent'; priorityLabel = 'Urgente'; } 
          html += `<div class="announcement-banner ${priorityClass}"><div class="announcement-title"><span>${a.title}</span><span class="priority-tag">${priorityLabel}</span></div><div class="announcement-message">${a.message}</div></div>`; 
        }); 
        html += '</div>'; 
        return html; 
      },
      renderAnnouncementsList: function() { if(!this.isAdmin) return; const content = document.getElementById('main-content'); let html = `<div style="display:flex; justify-content:space-between; margin-bottom:20px;"><h3>📢 Avisos</h3><button class="action-btn primary" onclick="app.abrirNovoAviso()">+ Novo</button></div><button class="btn-secondary" onclick="app.renderAdminPanel()">← Voltar</button>`; if(this.db.announcements.length===0) html += '<p>Nenhum aviso.</p>'; else { html += '<ul class="item-list">'; this.db.announcements.slice().reverse().forEach(a => { let priorityClass = 'priority-info', priorityLabel = 'Informativo'; if(a.priority === 'warning') { priorityClass = 'priority-warning'; priorityLabel = 'Atenção'; } else if(a.priority === 'urgent') { priorityClass = 'priority-urgent'; priorityLabel = 'Urgente'; } html += `<li class="item-card"><div><h4>${a.title}</h4><span>${priorityLabel}</span><button onclick="app.editarAviso(${a.id})">✏️</button><button onclick="app.excluirAviso(${a.id})">🗑️</button></div><p>${a.message}</p><p>Vigência: ${a.startDate||'?'} até ${a.endDate||'?'}</p></li>`; }); html += '</ul>'; } content.innerHTML = html; this.renderBottomNav('admin'); },
      abrirNovoAviso: function() { document.getElementById('aviso-id').value = ""; document.getElementById('aviso-titulo').value = ""; document.getElementById('aviso-mensagem').value = ""; document.getElementById('aviso-inicio').value = ""; document.getElementById('aviso-termino').value = ""; document.getElementById('aviso-prioridade').value = 'info'; document.getElementById('modal-aviso-title').innerText = 'Novo Aviso'; this.openModal('modal-aviso'); },
      editarAviso: function(id) { const aviso = this.db.announcements.find(a => a.id === id); if(!aviso) return; document.getElementById('aviso-id').value = aviso.id; document.getElementById('aviso-titulo').value = aviso.title; document.getElementById('aviso-mensagem').value = aviso.message; document.getElementById('aviso-inicio').value = aviso.startDate || ""; document.getElementById('aviso-termino').value = aviso.endDate || ""; document.getElementById('aviso-prioridade').value = aviso.priority || 'info'; document.getElementById('modal-aviso-title').innerText = 'Editar Aviso'; this.openModal('modal-aviso'); },
      salvarAviso: function() { const id = document.getElementById('aviso-id').value; const titulo = document.getElementById('aviso-titulo').value.trim(); const mensagem = document.getElementById('aviso-mensagem').value.trim(); const inicio = document.getElementById('aviso-inicio').value || null; const termino = document.getElementById('aviso-termino').value || null; const prioridade = document.getElementById('aviso-prioridade').value; if(!titulo||!mensagem) { alert('Preencha título e mensagem'); return; } if(inicio && termino && inicio > termino) { alert('Datas inválidas'); return; } const aviso = { id: id ? parseInt(id) : Date.now(), title: titulo, message: mensagem, startDate: inicio, endDate: termino, priority: prioridade }; if(id) { const index = this.db.announcements.findIndex(a => a.id === parseInt(id)); if(index!==-1) this.db.announcements[index] = aviso; } else { this.db.announcements.push(aviso); } this.saveDatabase(); this.closeModal('modal-aviso'); this.renderAdminPanel(); alert('Aviso salvo!'); },
      excluirAviso: function(id) { if(confirm('Excluir?')) { this.db.announcements = this.db.announcements.filter(a => a.id !== id); this.saveDatabase(); this.renderAnnouncementsList(); } },
      renderCatalog: function() { const content = document.getElementById('main-content'); let html = this.renderActiveAnnouncements(); html += `<div class="download-banner" onclick="window.open('https://drive.google.com/file/d/1JLq8a4Ukitz-20H8m-TjdF6EJ8ZDV9VG/view?usp=sharing', '_blank')"><div class="download-banner-icon">📘</div><div><h3>Baixe nossa cartilha</h3><p>Guia rápido</p></div></div><div style="margin-bottom:20px;"><input type="text" placeholder="Buscar material..." style="width:100%; padding:16px; background:rgba(0,0,0,0.3); border:1px solid var(--glass-border); border-radius:28px; color:white;" onkeyup="app.filterCatalog(event)"></div><div class="category-filters" id="category-filters"></div><div class="catalog-grid" id="catalog-grid"></div>`; content.innerHTML = html; this.renderCategoryFilters(); this.renderCatalogGrid(); this.renderBottomNav('catalog'); },
      renderCategoryFilters: function() { const container = document.getElementById('category-filters'); if(!container) return; const categories = ['Todos', ...this.db.categories]; const iconMap = { 'Todos':'📦', 'Papelaria':'📄', 'Informática':'💻', 'Limpeza':'🧹', 'Materiais de escritório':'✏️', 'Higiene':'🧼', 'Manutenção':'🔧' }; let chips = ''; categories.forEach(cat => { const icon = iconMap[cat] || '📦'; chips += `<div class="filter-chip ${cat==='Todos'?'active':''}" data-category="${cat==='Todos'?'all':cat}" onclick="app.filterCatalogByCategory('${cat==='Todos'?'all':cat}', event)"><span>${icon}</span> ${cat}</div>`; }); container.innerHTML = chips; },
      renderCatalogGrid: function() { const grid = document.getElementById('catalog-grid'); if(!grid) return; let html = ''; this.db.products.forEach(p => { if(p.category === 'Água mineral' || p.name.includes('Água Mineral')) return; const status = p.stock===0 ? 'zero' : (p.stock<=p.minStock ? 'low' : 'normal'); const statusText = p.stock===0 ? 'Zerado' : (p.stock<=p.minStock ? 'Baixo' : 'Normal'); html += `<div class="product-card" data-category="${p.category}" data-name="${p.name.toLowerCase()}"><div class="product-image">${p.imageBase64 ? `<img src="${p.imageBase64}" style="width:100%; height:100%; object-fit:cover;">` : (p.imageEmoji || '📦')}</div><div class="product-info"><h4>${p.name}</h4><div class="product-category">${p.category}</div><div class="product-desc">${p.description}</div><div class="product-stock"><span>${p.stock} ${p.unit}</span><span class="stock-badge ${status}">${statusText}</span></div><button class="btn-cart" onclick="app.addToCart(${p.id})" ${p.stock===0?'disabled':''}>➕ Adicionar</button></div></div>`; }); grid.innerHTML = html; },
      filterCatalog: function(e) { const search = e.target.value.toLowerCase(); document.querySelectorAll('.product-card').forEach(card => { card.style.display = card.dataset.name.includes(search) ? 'block' : 'none'; }); },
      filterCatalogByCategory: function(category, event) { document.querySelectorAll('.product-card').forEach(card => { card.style.display = (category==='all' || card.dataset.category === category) ? 'block' : 'none'; }); document.querySelectorAll('.filter-chip').forEach(chip => chip.classList.remove('active')); if(event && event.target.closest('.filter-chip')) event.target.closest('.filter-chip').classList.add('active'); },
      addToCart: function(productId) { const product = this.db.products.find(p => p.id === productId); if(!product || product.stock<=0) return; const existing = this.cart.find(i => i.productId === productId); if(existing) { if(existing.qty < product.stock) existing.qty++; else { this.showNotification('Quantidade máxima!'); return; } } else { this.cart.push({ productId, name: product.name, unit: product.unit, qty: 1, maxStock: product.stock, imageEmoji: product.imageEmoji, imageBase64: product.imageBase64 }); } this.updateCartCount(); this.saveCart(); this.showNotification('Item adicionado!'); },
      showNotification: function(msg) { const toast = document.getElementById('toast-notification'); toast.textContent = msg; toast.classList.add('show'); setTimeout(() => toast.classList.remove('show'), 2000); },
      updateCartCount: function() { const count = this.cart.reduce((acc,i)=>acc+i.qty,0); const badge = document.getElementById('cart-count'); if(count>0) { badge.style.display='flex'; badge.innerHTML=count; } else badge.style.display='none'; },
      openCart: function() { this.renderCartItems(); document.getElementById('cart-overlay').classList.add('active'); },
      closeCart: function() { document.getElementById('cart-overlay').classList.remove('active'); },
      renderCartItems: function() { const container = document.getElementById('cart-items'); const totalSpan = document.getElementById('total-items'); let html = ''; let total = 0; this.cart.forEach(item => { total += item.qty; html += `<div class="cart-item"><div class="cart-item-icon">${item.imageBase64 ? `<img src="${item.imageBase64}">` : (item.imageEmoji || '📦')}</div><div><h4>${item.name}</h4><p>${item.unit} | Disp: ${item.maxStock}</p></div><div class="cart-item-actions"><button onclick="app.decrementCartItem(${item.productId})">-</button><span>${item.qty}</span><button onclick="app.incrementCartItem(${item.productId})">+</button><button onclick="app.removeFromCart(${item.productId})">🗑️</button></div></div>`; }); if(this.cart.length===0) html = '<p style="text-align:center; padding:30px;">Carrinho vazio</p>'; container.innerHTML = html; totalSpan.innerHTML = total; },
      incrementCartItem: function(pid) { const item = this.cart.find(i=>i.productId===pid); const prod = this.db.products.find(p=>p.id===pid); if(item && prod && item.qty < prod.stock) { item.qty++; this.updateCartCount(); this.renderCartItems(); this.saveCart(); } else this.showNotification('Quantidade máxima'); },
      decrementCartItem: function(pid) { const item = this.cart.find(i=>i.productId===pid); if(item) { if(item.qty>1) { item.qty--; this.updateCartCount(); this.renderCartItems(); this.saveCart(); } else this.removeFromCart(pid); } },
      removeFromCart: function(pid) { this.cart = this.cart.filter(i=>i.productId!==pid); this.updateCartCount(); this.renderCartItems(); this.saveCart(); },
      clearCart: function() { if(confirm('Limpar carrinho?')) { this.cart = []; this.updateCartCount(); this.renderCartItems(); this.saveCart(); } },
      saveCart: function() { localStorage.setItem('almoxCart', JSON.stringify(this.cart)); },
      loadCart: function() { const saved = localStorage.getItem('almoxCart'); if(saved) { try { this.cart = JSON.parse(saved); this.updateCartCount(); } catch(e) { this.cart = []; } } },
      openCheckoutModal: async function() { if(this.cart.length===0) { alert('Carrinho vazio'); return; } this.openModal('modal-checkout'); const setorGroup = document.getElementById('pedido-setor-group'); setorGroup.innerHTML = '<label>Setor *</label><span>Carregando...</span>'; document.getElementById('outro-setor-group').style.display = 'none'; const selectHtml = await this.renderSetorDropdown('pedido-setor', 'outro-setor-group', 'pedido-setor-outro', true); setorGroup.innerHTML = `<label>Setor *</label> ${selectHtml}`; },
      finalizarPedido: async function() { const nome = document.getElementById('pedido-nome').value.trim(); const email = document.getElementById('pedido-email').value.trim(); const setor = this.getSetorValue('pedido-setor', 'pedido-setor-outro'); const obs = document.getElementById('pedido-obs').value.trim(); if(!nome||!email||!setor) { alert('Preencha todos os campos'); return; } const trackingCode = 'MAT-' + Date.now().toString(36).toUpperCase() + '-' + Math.floor(Math.random()*1000).toString().padStart(3,'0'); const pedido = { id: Date.now(), trackingCode, date: new Date().toISOString().split('T')[0], requesterName: nome, email, sector: setor, observation: obs, items: this.cart.map(i => ({ productId: i.productId, productName: i.name, qty: i.qty, unit: i.unit })), status: 'pendente' }; this.db.requests.push(pedido); this.saveDatabase(); await this.salvarDados('pedidosMateriais', pedido); this.gerarPDFPedidoMaterial(pedido); this.baixarPDFRecente(); this.cart = []; this.saveCart(); this.updateCartCount(); this.closeCart(); this.closeModal('modal-checkout'); document.getElementById('tracking-code-display').innerText = trackingCode; this.openModal('modal-pedido-realizado'); },
      renderSolicitarAgua: async function() { const content = document.getElementById('main-content'); const aguaProduct = this.db.products.find(p=>p.name==='Água Mineral'||p.category==='Água mineral'); const estoque = aguaProduct ? aguaProduct.stock : 0; let html = this.renderActiveAnnouncements() + `<div><h2>💧 Solicitar Água Mineral</h2><p>Preencha os dados</p></div><div class="water-stock-control"><div>Estoque: <strong>${estoque}</strong> garrafões</div><form id="form-agua-solicitacao"><div class="form-group"><label>Nome *</label><input type="text" id="agua-nome" required></div><div class="form-group"><label>E-mail *</label><input type="email" id="agua-email" required></div><div class="form-group" id="agua-setor-group"><label>Setor *</label><span>Carregando...</span></div><div class="form-group" id="agua-outro-setor-group" style="display:none;"><label>Digite o setor</label><input type="text" id="agua-setor-outro"></div><div class="form-group"><label>Local entrega *</label><input type="text" id="agua-local" required></div><div class="form-group"><label>Complemento</label><input type="text" id="agua-complemento"></div><div class="form-group"><label>Quantidade *</label><input type="number" id="agua-quantidade" min="1" value="1" required></div><div class="form-group"><label>Validade garrafão vazio</label><input type="date" id="agua-validade"></div><div class="form-group"><label>Observações</label><textarea id="agua-obs" rows="2"></textarea></div><button type="submit" class="btn-primary" onclick="event.preventDefault(); app.enviarSolicitacaoAgua();">Solicitar</button></form></div><div><canvas id="graficoAgua" height="150"></canvas></div>`; content.innerHTML = html; if(aguaProduct) this.atualizarGraficoAgua(aguaProduct.stock); this.renderBottomNav('agua'); const selectHtml = await this.renderSetorDropdown('agua-setor', 'agua-outro-setor-group', 'agua-setor-outro', true); document.getElementById('agua-setor-group').innerHTML = `<label>Setor *</label> ${selectHtml}`; },
      enviarSolicitacaoAgua: async function() { const nome = document.getElementById('agua-nome').value.trim(); const email = document.getElementById('agua-email').value.trim(); const setor = this.getSetorValue('agua-setor', 'agua-setor-outro'); const local = document.getElementById('agua-local').value.trim(); const quantidade = parseInt(document.getElementById('agua-quantidade').value); const validade = document.getElementById('agua-validade').value; const obs = document.getElementById('agua-obs').value.trim(); if(!nome||!email||!setor||!local) { alert('Preencha todos os campos'); return; } const codigo = 'AGUA-' + Date.now().toString(36).toUpperCase() + '-' + Math.floor(Math.random()*1000).toString().padStart(3,'0'); const solicitacao = { id: Date.now(), codigo, data: new Date().toISOString().split('T')[0], nome, email, setor, local, complemento: document.getElementById('agua-complemento').value.trim(), quantidade, validade: validade||null, observacoes: obs, status:'pendente', historico:[{ data: new Date().toISOString(), acao:'Solicitação criada', status:'pendente' }] }; this.db.waterRequests.push(solicitacao); this.saveDatabase(); await this.salvarDados('pedidosAgua', solicitacao); this.gerarPDFPedidoAgua(solicitacao); this.baixarPDFRecente(); document.getElementById('tracking-code-display').innerText = codigo; this.openModal('modal-pedido-realizado'); document.getElementById('form-agua-solicitacao').reset(); document.getElementById('agua-outro-setor-group').style.display = 'none'; },
      gerarPDFPedidoAgua: function(s) { const {jsPDF}=window.jspdf; const doc=new jsPDF(); doc.setFontSize(18); doc.text('Solicitação de Água Mineral',14,22); doc.setFontSize(12); doc.text(`Código: ${s.codigo}`,14,32); doc.text(`Data: ${s.data}`,14,40); doc.setFontSize(14); doc.text('Dados do Solicitante',14,52); doc.setFontSize(10); doc.text(`Nome: ${s.nome}`,14,62); doc.text(`E-mail: ${s.email}`,14,70); doc.text(`Setor: ${s.setor}`,14,78); doc.setFontSize(14); doc.text('Detalhes',14,92); doc.setFontSize(10); doc.text(`Local: ${s.local} ${s.complemento||''}`,14,102); doc.text(`Quantidade: ${s.quantidade} garrafão(ões)`,14,110); if(s.validade) doc.text(`Validade: ${s.validade}`,14,118); if(s.observacoes) doc.text(`Observações: ${s.observacoes}`,14,126); doc.text(`Status: ${s.status}`,14,140); const pdfBase64=doc.output('dataurlstring'); s.pdfBase64=pdfBase64; this.recentPDF=pdfBase64; this.saveDatabase(); return pdfBase64; },
      gerarPDFPedidoMaterial: function(p) { const {jsPDF}=window.jspdf; const doc=new jsPDF(); doc.setFontSize(18); doc.text('Solicitação de Materiais',14,22); doc.setFontSize(12); doc.text(`Código: ${p.trackingCode}`,14,32); doc.text(`Data: ${p.date}`,14,40); doc.setFontSize(14); doc.text('Dados do Solicitante',14,52); doc.setFontSize(10); doc.text(`Nome: ${p.requesterName}`,14,62); doc.text(`E-mail: ${p.email}`,14,70); doc.text(`Setor: ${p.sector}`,14,78); doc.setFontSize(14); doc.text('Itens',14,92); doc.autoTable({ startY:100, head:[['Produto','Qtd','Unidade']], body:p.items.map(i=>[i.productName,i.qty,i.unit]), theme:'striped', headStyles:{fillColor:[10,75,140]} }); if(p.observation) doc.text(`Observações: ${p.observation}`,14,doc.lastAutoTable.finalY+10); doc.text(`Status: ${p.status}`,14,doc.lastAutoTable.finalY+20); const pdfBase64=doc.output('dataurlstring'); p.pdfBase64=pdfBase64; this.recentPDF=pdfBase64; this.saveDatabase(); return pdfBase64; },
      baixarPDFRecente: function() { if(!this.recentPDF) { alert('Nenhum PDF disponível'); return; } const link=document.createElement('a'); link.href=this.recentPDF; link.download='solicitacao.pdf'; link.click(); },
      enviarPDFEmail: function() { alert('Funcionalidade de envio por e-mail simulada.'); },
      renderMinhasSolicitacoesAgua: function() { const content=document.getElementById('main-content'); content.innerHTML=`<h3>💧 Minhas Solicitações</h3><button class="btn-secondary" onclick="app.renderSolicitarAgua()">← Nova</button><div><input type="text" id="filtro-nome-agua" placeholder="Filtrar pelo nome" style="width:100%; padding:12px; background:rgba(0,0,0,0.3); border-radius:28px;" onkeyup="app.filtrarMinhasSolicitacoesAgua()"></div><div id="lista-minhas-solicitacoes"></div>`; this.filtrarMinhasSolicitacoesAgua(); this.renderBottomNav('minhas-solicitacoes'); },
      filtrarMinhasSolicitacoesAgua: function() { const filtro=document.getElementById('filtro-nome-agua')?.value.toLowerCase()||''; const solicitacoes=this.db.waterRequests.filter(s=>s.nome.toLowerCase().includes(filtro)).slice().reverse(); const container=document.getElementById('lista-minhas-solicitacoes'); if(!container) return; let html=''; if(solicitacoes.length===0) html='<p>Nenhuma solicitação.</p>'; else solicitacoes.forEach(s=>{ let statusClass='',statusText=s.status; if(s.status==='pendente') { statusClass='status-pendente'; statusText='Pendente'; } else if(s.status==='aprovado') { statusClass='status-aprovado'; statusText='Aprovado'; } else if(s.status==='entregue') { statusClass='status-entregue'; statusText='Entregue'; } else if(s.status==='confirmado') { statusClass='status-confirmado'; statusText='Confirmado'; } else if(s.status==='negado') { statusClass='status-negado'; statusText='Negado'; } else if(s.status==='aguardando_reposicao') { statusClass='status-aguardando'; statusText='Aguardando Reposição'; } html+=`<div class="item-card"><div><strong>${s.codigo}</strong><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Data: ${s.data}</p><p>Setor: ${s.setor} | Qtd: ${s.quantidade}</p><p>Local: ${s.local}</p><button class="action-btn" onclick="app.verDetalhesAgua(${s.id})">Ver detalhes</button></div>`; }); container.innerHTML=html; },
      verDetalhesAgua: async function(id) { const s=this.db.waterRequests.find(r=>r.id===id); if(!s) return; let queueHtml=''; if(s.status==='pendente'||s.status==='aguardando_reposicao') { const queueInfo=await this.consultarPosicaoFila(s.codigo); if(queueInfo.success && queueInfo.position) queueHtml=`<p><strong>Posição na fila:</strong> ${queueInfo.position} de ${queueInfo.totalPending}</p>`; } const body=document.getElementById('detalhes-agua-body'); let historicoHtml=''; if(s.historico) historicoHtml='<h4>Histórico</h4><ul>'+s.historico.map(h=>`<li>${new Date(h.data).toLocaleString()}: ${h.acao}</li>`).join('')+'</ul>'; let statusClass=`status-${s.status}`; body.innerHTML=`<p><strong>Código:</strong> ${s.codigo}</p><p><strong>Data:</strong> ${s.data}</p>${queueHtml}<p><strong>Nome:</strong> ${s.nome}</p><p><strong>E-mail:</strong> ${s.email}</p><p><strong>Setor:</strong> ${s.setor}</p><p><strong>Local:</strong> ${s.local} ${s.complemento||''}</p><p><strong>Quantidade:</strong> ${s.quantidade}</p><p><strong>Validade:</strong> ${s.validade||'Não informada'}</p><p><strong>Observações:</strong> ${s.observacoes||'-'}</p><p><strong>Status:</strong> <span class="tracking-status ${statusClass}">${s.status.toUpperCase()}</span></p>${historicoHtml}${s.status==='entregue'?`<button class="btn-primary" onclick="app.confirmarRecebimentoAgua(${s.id})">✅ Confirmar Recebimento</button>`:''}${s.pdfBase64?`<button class="btn-primary" onclick="window.open('${s.pdfBase64}')">📥 PDF</button>`:''}`; this.openModal('modal-detalhes-agua'); },
      confirmarRecebimentoAgua: function(id) { const req=this.db.waterRequests.find(r=>r.id===id); if(!req||req.status!=='entregue') return; req.status='confirmado'; req.historico.push({data:new Date().toISOString(), acao:`Recebimento confirmado por ${this.currentUser?.name||'Solicitante'}`, status:'confirmado'}); this.saveDatabase(); this.salvarDados('pedidosAgua',req); alert('Recebimento confirmado!'); this.closeModal('modal-detalhes-agua'); if(document.getElementById('lista-minhas-solicitacoes')) this.filtrarMinhasSolicitacoesAgua(); else if(document.getElementById('main-content').innerHTML.includes('Solicitações')) this.abrirGerenciarSolicitacoesAgua(); },
      renderTrackOrder: function() { const content=document.getElementById('main-content'); content.innerHTML=`<div class="tracking-container"><h3>🔍 Rastrear Pedido</h3><div class="tracking-input-group"><input type="text" id="tracking-input" placeholder="Código" style="flex:1; background:rgba(0,0,0,0.3); border-radius:28px; padding:14px;"><button onclick="app.trackOrder()" class="btn-primary">Buscar</button></div><div id="tracking-result" class="tracking-result" style="display:none;"></div></div>`; this.renderBottomNav('track'); },
      trackOrder: function() { const code=document.getElementById('tracking-input').value.trim().toUpperCase(); if(!code) { alert('Digite um código'); return; } let pedido=this.db.requests.find(r=>r.trackingCode===code); let tipo='material'; if(!pedido) { pedido=this.db.waterRequests.find(r=>r.codigo===code); tipo='agua'; } const resultDiv=document.getElementById('tracking-result'); if(!pedido) { resultDiv.style.display='block'; resultDiv.innerHTML='<p>Código não encontrado.</p>'; return; } if(tipo==='material') { const statusClass=pedido.status==='pendente'?'status-pendente':(pedido.status==='aprovado'?'status-aprovado':'status-negado'); const statusText=pedido.status==='pendente'?'Pendente':(pedido.status==='aprovado'?'Aprovado':'Negado'); let itemsHtml=''; pedido.items.forEach(i=>{ itemsHtml+=`<div><span>${i.productName}</span><span>${i.qty} ${i.unit}</span></div>`; }); resultDiv.innerHTML=`<div><span>${pedido.trackingCode}</span><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Solicitante: ${pedido.requesterName}</p><p>Setor: ${pedido.sector}</p><p>Data: ${pedido.date}</p><div><h4>Itens</h4>${itemsHtml}</div>`; } else { let statusClass=''; let statusText=pedido.status; if(pedido.status==='pendente') { statusClass='status-pendente'; statusText='Pendente'; } else if(pedido.status==='aprovado') { statusClass='status-aprovado'; statusText='Aprovado'; } else if(pedido.status==='entregue') { statusClass='status-entregue'; statusText='Entregue'; } else if(pedido.status==='confirmado') { statusClass='status-confirmado'; statusText='Confirmado'; } else if(pedido.status==='negado') { statusClass='status-negado'; statusText='Negado'; } else if(pedido.status==='aguardando_reposicao') { statusClass='status-aguardando'; statusText='Aguardando Reposição'; } resultDiv.innerHTML=`<div><span>${pedido.codigo}</span><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Solicitante: ${pedido.nome}</p><p>Local: ${pedido.local}</p><p>Quantidade: ${pedido.quantidade}</p><p>Data: ${pedido.data}</p><div><h4>Histórico</h4>${pedido.historico?pedido.historico.map(h=>`<div>${new Date(h.data).toLocaleString()}: ${h.acao}</div>`).join(''):''}</div>`; } resultDiv.style.display='block'; },
      updateWaterStock: function(op) { if(!this.isAdmin) { this.showNotification('Acesso negado'); return; } const qty=parseInt(document.getElementById('water-stock-qty').value); if(isNaN(qty)||qty<=0) { this.showNotification('Quantidade inválida'); return; } const aguaProduct=this.db.products.find(p=>p.name.includes('Água')||p.category==='Água mineral'); if(!aguaProduct) return; if(op==='add') { aguaProduct.stock+=qty; this.db.waterStockMovements.push({data:new Date().toISOString(), tipo:'adição', quantidade:qty, estoqueResultante:aguaProduct.stock, usuario:this.currentUser?.name||'Admin'}); } else if(op==='remove') { if(aguaProduct.stock<qty) { this.showNotification('Estoque insuficiente'); return; } aguaProduct.stock-=qty; this.db.waterStockMovements.push({data:new Date().toISOString(), tipo:'remoção', quantidade:qty, estoqueResultante:aguaProduct.stock, usuario:this.currentUser?.name||'Admin'}); } this.saveDatabase(); this.showNotification(`Estoque atualizado: ${aguaProduct.stock}`); if(document.getElementById('form-agua-solicitacao')) this.renderSolicitarAgua(); else this.renderAdminPanel(); },
      renderAdminWaterStock: function() { const aguaProduct=this.db.products.find(p=>p.name.includes('Água')||p.category==='Água mineral'); const estoque=aguaProduct?aguaProduct.stock:0; const movimentos=this.db.waterStockMovements.slice().reverse().slice(0,10); return `<div class="water-stock-control"><h3>💧 Controle Estoque Água</h3><div>Estoque: <strong>${estoque}</strong> garrafões</div><div><input type="number" id="water-stock-qty" min="1" value="1"><button onclick="app.updateWaterStock('add')">+ Adicionar</button><button onclick="app.updateWaterStock('remove')">- Remover</button></div><div><h4>Últimas movimentações</h4>${movimentos.length?movimentos.map(m=>`<div>${new Date(m.data).toLocaleString()}: ${m.tipo} ${m.quantidade}</div>`).join(''):'<p>Nenhuma</p>'}</div></div>`; },
      renderAdminPanel: function() { if(!this.isAdmin) return; const aguaProduct=this.db.products.find(p=>p.name.includes('Água')||p.category==='Água mineral'); const estoqueAgua=aguaProduct?aguaProduct.stock:0; const pendentes=this.db.waterRequests.filter(r=>r.status==='pendente').length; const aprovados=this.db.waterRequests.filter(r=>r.status==='aprovado').length; const entregues=this.db.waterRequests.filter(r=>r.status==='entregue').length; const confirmados=this.db.waterRequests.filter(r=>r.status==='confirmado').length; const negados=this.db.waterRequests.filter(r=>r.status==='negado').length; const aguardando=this.db.waterRequests.filter(r=>r.status==='aguardando_reposicao').length; const setores={}; this.db.waterRequests.forEach(r=>{ if(r.status==='entregue'||r.status==='aprovado'||r.status==='confirmado') setores[r.setor]=(setores[r.setor]||0)+r.quantidade; }); const topSetores=Object.entries(setores).sort((a,b)=>b[1]-a[1]).slice(0,3).map(([s,q])=>`${s}:${q}`).join(', ')||'Nenhum'; const content=document.getElementById('main-content'); let html=`<div style="display:flex; gap:10px; flex-wrap:wrap;"><button class="action-btn primary" onclick="app.abrirNovoProduto()">➕ Produto</button><button class="action-btn" onclick="app.abrirGerenciarSolicitacoesAgua()">💧 Água</button><button class="action-btn" onclick="app.renderAnnouncementsList()">📢 Avisos</button><button class="action-btn" onclick="app.abrirListaTodosPedidos()">📦 Pedidos</button><button class="action-btn" onclick="app.renderAdminOuvidoria()">📬 Ouvidoria</button><button class="action-btn" onclick="app.renderQRInventory()">📱 QR</button><button class="action-btn primary" onclick="app.abrirGerenciarUsuarios()">👥 Usuários</button></div><h3>📊 Dashboard Água</h3><div class="dashboard-cards"><div><div>${estoqueAgua}</div><div>Garrafões</div></div><div><div>${pendentes}</div><div>Pendentes</div></div><div><div>${aguardando}</div><div>Aguardando</div></div><div><div>${aprovados}</div><div>Aprovados</div></div><div><div>${entregues+confirmados}</div><div>Entregues/Conf.</div></div><div><div>${negados}</div><div>Negados</div></div><div><div>${topSetores}</div><div>Consumo por setor</div></div></div>${this.renderAdminWaterStock()}<h3>📦 Produtos</h3><ul id="admin-product-list">`; this.db.products.forEach(p=>{ html+=`<li class="item-card"><div>${p.imageBase64?`<img src="${p.imageBase64}" style="width:50px;">`:(p.imageEmoji||'📦')}</div><div><h4>${p.name}</h4><div>Estoque: ${p.stock} ${p.unit}</div></div><div><button onclick="app.editarProduto(${p.id})">✏️</button><button onclick="app.excluirProduto(${p.id})">🗑️</button></div></li>`; }); html+='</ul>'; content.innerHTML=html; this.renderBottomNav('admin'); },
      abrirGerenciarUsuarios: function() { let html='<ul>'; this.db.users.forEach(u=>{ html+=`<li class="item-card"><div><strong>${u.name}</strong> (${u.email})</div><div><label>Permissão: ${u.role}</label><select onchange="app.salvarPermissaoUsuario(${u.id}, this.value)"><option value="admin" ${u.role==='admin'?'selected':''}>Admin</option><option value="entregador" ${u.role==='entregador'?'selected':''}>Entregador</option><option value="solicitante" ${u.role==='solicitante'||u.role==='user'?'selected':''}>Solicitante</option></select></div></li>`; }); html+='</ul>'; document.getElementById('usuarios-body').innerHTML=html; this.openModal('modal-usuarios'); },
      salvarPermissaoUsuario: function(id,newRole) { const user=this.db.users.find(u=>u.id===id); if(user) { user.role=newRole; this.saveDatabase(); alert(`Permissão alterada para ${newRole}.`); } },
      abrirGerenciarSolicitacoesAgua: function() { if(!this.isAdmin&&!this.isEntregador) return; const content=document.getElementById('main-content'); let html=`<div><h3>💧 Solicitações de Água</h3>${this.isAdmin?`<button class="btn-secondary" onclick="app.renderAdminPanel()">← Voltar</button>`:''}</div>`; const pendentes=this.db.waterRequests.filter(r=>r.status==='pendente'); const aguardando=this.db.waterRequests.filter(r=>r.status==='aguardando_reposicao'); const aprovadas=this.db.waterRequests.filter(r=>r.status==='aprovado'); const entregues=this.db.waterRequests.filter(r=>r.status==='entregue'||r.status==='confirmado'); const negadas=this.db.waterRequests.filter(r=>r.status==='negado'); if(pendentes.length===0&&aguardando.length===0&&aprovadas.length===0&&entregues.length===0&&negadas.length===0) html+='<p>Nenhuma solicitação.</p>'; else { if(aprovadas.length>0) { html+='<h4>✅ Aprovadas</h4>'; aprovadas.forEach(s=>html+=this.renderSolicitacaoAguaCard(s)); } if(this.isAdmin) { if(pendentes.length>0) { html+='<h4>⏳ Pendentes</h4>'; pendentes.forEach(s=>html+=this.renderSolicitacaoAguaCard(s)); } if(aguardando.length>0) { html+='<h4>🔄 Aguardando Reposição</h4>'; aguardando.forEach(s=>html+=this.renderSolicitacaoAguaCard(s)); } if(entregues.length>0) { html+='<h4>📦 Entregues/Confirmadas</h4>'; entregues.forEach(s=>html+=this.renderSolicitacaoAguaCard(s)); } if(negadas.length>0) { html+='<h4>❌ Negadas</h4>'; negadas.forEach(s=>html+=this.renderSolicitacaoAguaCard(s)); } } } content.innerHTML=html; this.renderBottomNav('entregas'); },
      renderSolicitacaoAguaCard: function(s) { let statusClass='',statusText=s.status; if(s.status==='pendente') { statusClass='status-pendente'; statusText='Pendente'; } else if(s.status==='aprovado') { statusClass='status-aprovado'; statusText='Aprovado'; } else if(s.status==='entregue') { statusClass='status-entregue'; statusText='Entregue'; } else if(s.status==='confirmado') { statusClass='status-confirmado'; statusText='Confirmado'; } else if(s.status==='negado') { statusClass='status-negado'; statusText='Negado'; } else if(s.status==='aguardando_reposicao') { statusClass='status-aguardando'; statusText='Aguardando Reposição'; } let actions=''; if(this.isAdmin&&(s.status==='pendente'||s.status==='aguardando_reposicao')) actions=`<button class="action-btn primary" onclick="app.aprovarSolicitacaoAgua(${s.id})">✅ Aprovar</button> <button class="btn-danger" onclick="app.negarSolicitacaoAgua(${s.id})">❌ Negar</button>`; else if((this.isAdmin||this.isEntregador)&&s.status==='aprovado') actions=`<button class="action-btn primary" onclick="app.registrarEntregaAgua(${s.id})">🚚 Registrar Entrega</button>`; else if((this.isAdmin||this.isEntregador)&&s.status==='entregue') actions=`<button class="action-btn primary" onclick="app.confirmarRecebimentoAgua(${s.id})">✅ Confirmar Recebimento</button>`; return `<div class="item-card"><div><strong>${s.codigo}</strong><span class="tracking-status ${statusClass}">${statusText.toUpperCase()}</span></div><p>Data: ${s.data}</p><p>Solicitante: ${s.nome} (${s.setor})</p><p>Local: ${s.local}</p><p>Quantidade: ${s.quantidade}</p><div>${actions}<button class="action-btn" onclick="app.verDetalhesAgua(${s.id})">🔍 Detalhes</button></div></div>`; },
      aprovarSolicitacaoAgua: function(id) { const req=this.db.waterRequests.find(r=>r.id===id); if(!req) return; const aguaProduct=this.db.products.find(p=>p.name.includes('Água')||p.category==='Água mineral'); if(!aguaProduct||aguaProduct.stock<req.quantidade) { alert('Estoque insuficiente'); return; } aguaProduct.stock-=req.quantidade; this.db.waterStockMovements.push({data:new Date().toISOString(), tipo:'remoção (aprovação)', quantidade:req.quantidade, estoqueResultante:aguaProduct.stock, usuario:this.currentUser?.name||'Admin', solicitacao:req.codigo}); req.status='aprovado'; req.historico.push({data:new Date().toISOString(), acao:'Solicitação aprovada.', status:'aprovado'}); this.saveDatabase(); this.salvarDados('pedidosAgua',req); this.abrirGerenciarSolicitacoesAgua(); alert(`Aprovada. Estoque restante: ${aguaProduct.stock}`); },
      negarSolicitacaoAgua: function(id) { if(confirm('Negar?')) { const req=this.db.waterRequests.find(r=>r.id===id); if(req) { req.status='negado'; req.historico.push({data:new Date().toISOString(), acao:'Negada', status:'negado'}); this.saveDatabase(); this.salvarDados('pedidosAgua',req); this.abrirGerenciarSolicitacoesAgua(); } } },
      registrarEntregaAgua: function(id) { const req=this.db.waterRequests.find(r=>r.id===id); if(req&&req.status==='aprovado') { req.status='entregue'; req.historico.push({data:new Date().toISOString(), acao:`Entrega registrada por ${this.currentUser?.name||'Entregador'}`, status:'entregue'}); this.saveDatabase(); this.salvarDados('pedidosAgua',req); this.abrirGerenciarSolicitacoesAgua(); alert('Entrega registrada!'); } },
      abrirNovoProduto: function() { document.getElementById('produto-id').value=''; document.getElementById('produto-nome').value=''; document.getElementById('produto-categoria').value=''; document.getElementById('produto-descricao').value=''; document.getElementById('produto-unidade').value='un'; document.getElementById('produto-estoque').value='0'; document.getElementById('produto-minstock').value='5'; document.getElementById('produto-localizacao').value=''; document.getElementById('produto-valor').value='0.00'; document.getElementById('produto-foto').value=''; const preview=document.getElementById('image-preview'); preview.style.backgroundImage=''; preview.innerHTML='<span>Pré-visualização</span>'; preview.classList.remove('has-image'); document.getElementById('modal-produto-title').innerText='➕ Novo Produto'; this.openModal('modal-produto'); },
      editarProduto: function(id) { const produto=this.db.products.find(p=>p.id===id); if(!produto) return; document.getElementById('produto-id').value=produto.id; document.getElementById('produto-nome').value=produto.name; document.getElementById('produto-categoria').value=produto.category||''; document.getElementById('produto-descricao').value=produto.description||''; document.getElementById('produto-unidade').value=produto.unit||'un'; document.getElementById('produto-estoque').value=produto.stock; document.getElementById('produto-minstock').value=produto.minStock||5; document.getElementById('produto-localizacao').value=produto.location||''; document.getElementById('produto-valor').value=produto.unitValue||0; const preview=document.getElementById('image-preview'); if(produto.imageBase64) { preview.style.backgroundImage=`url('${produto.imageBase64}')`; preview.innerHTML='<span>Foto atual</span>'; preview.classList.add('has-image'); } else { preview.style.backgroundImage=''; preview.innerHTML='<span>Pré-visualização</span>'; preview.classList.remove('has-image'); } document.getElementById('produto-foto').value=''; document.getElementById('modal-produto-title').innerText='✏️ Editar Produto'; this.openModal('modal-produto'); },
      salvarProduto: function() { const id=document.getElementById('produto-id').value; const nome=document.getElementById('produto-nome').value.trim(); if(!nome) { alert('Nome obrigatório'); return; } const fileInput=document.getElementById('produto-foto'); const salvar=(base64)=>{ const produto={ id:id?parseInt(id):Date.now(), name:nome, category:document.getElementById('produto-categoria').value||'Outros', description:document.getElementById('produto-descricao').value.trim(), unit:document.getElementById('produto-unidade').value.trim()||'un', stock:parseInt(document.getElementById('produto-estoque').value)||0, minStock:parseInt(document.getElementById('produto-minstock').value)||5, location:document.getElementById('produto-localizacao').value.trim(), unitValue:parseFloat(document.getElementById('produto-valor').value)||0, imageEmoji:'📦', imageBase64:base64 }; if(id) { const idx=this.db.products.findIndex(p=>p.id===parseInt(id)); if(idx!==-1) { if(!base64) produto.imageBase64=this.db.products[idx].imageBase64; this.db.products[idx]=produto; } } else this.db.products.push(produto); this.saveDatabase(); this.closeModal('modal-produto'); this.renderAdminPanel(); this.renderCatalog(); }; if(fileInput.files.length>0) { const reader=new FileReader(); reader.onload=e=>salvar(e.target.result); reader.readAsDataURL(fileInput.files[0]); } else salvar(null); },
      excluirProduto: function(id) { if(confirm('Excluir produto?')) { this.db.products=this.db.products.filter(p=>p.id!==id); this.saveDatabase(); this.renderAdminPanel(); this.renderCatalog(); } },
      abrirListaTodosPedidos: function() { if(!this.isAdmin) return; const content=document.getElementById('main-content'); let html=`<h3>📋 Todos os Pedidos (Materiais)</h3><button class="btn-secondary" onclick="app.renderAdminPanel()">← Voltar</button>`; if(this.db.requests.length===0) html+='<p>Nenhum pedido.</p>'; else this.db.requests.slice().reverse().forEach(r=>{ const statusClass=r.status==='pendente'?'status-pendente':(r.status==='aprovado'?'status-aprovado':'status-negado'); const statusText=r.status==='pendente'?'Pendente':(r.status==='aprovado'?'Aprovado':'Negado'); html+=`<div class="item-card"><div><strong>${r.trackingCode}</strong><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Solicitante: ${r.requesterName} (${r.sector})</p><p>Itens: ${r.items.length} | Data: ${r.date}</p><div><button class="btn-primary" onclick="app.aprovarPedidoAdmin(${r.id})">✅ Aprovar</button><button class="btn-danger" onclick="app.excluirPedidoAdmin(${r.id})">🗑️ Excluir</button>${r.pdfBase64?`<button class="action-btn" onclick="window.open('${r.pdfBase64}')">📄 PDF</button>`:''}</div></div>`; }); content.innerHTML=html; },
      aprovarPedidoAdmin: function(requestId) { const req=this.db.requests.find(r=>r.id===requestId); if(req) { req.status='aprovado'; req.items.forEach(item=>{ const prod=this.db.products.find(p=>p.id===item.productId); if(prod) prod.stock-=item.qty; }); this.saveDatabase(); this.salvarDados('pedidosMateriais',req); this.abrirListaTodosPedidos(); alert('Pedido aprovado!'); } },
      excluirPedidoAdmin: function(requestId) { if(confirm('Excluir pedido?')) { this.db.requests=this.db.requests.filter(r=>r.id!==requestId); this.saveDatabase(); this.abrirListaTodosPedidos(); } },
      renderOuvidoriaMenu: function() { const content=document.getElementById('main-content'); content.innerHTML=`<h3>📢 Ouvidoria</h3><div class="ouvidoria-menu"><div class="ouvidoria-card" onclick="app.openModal('modal-manifestacao')"><div>📝</div><div><h4>Registrar manifestação</h4><p>Reclamação, sugestão, elogio...</p></div></div><div class="ouvidoria-card" onclick="app.renderMinhasManifestacoes()"><div>👤</div><div><h4>Minhas manifestações</h4><p>Acompanhe</p></div></div><div class="ouvidoria-card" onclick="app.renderAcompanharManifestacaoPorCodigo()"><div>🔍</div><div><h4>Acompanhar por código</h4><p>Informe o protocolo</p></div></div></div><div><h4>❓ Perguntas frequentes</h4><div class="faq-item" onclick="app.sugerirResposta('Como faço para solicitar material?')">Como solicitar material?</div><div class="faq-item" onclick="app.sugerirResposta('Onde vejo o andamento do meu pedido?')">Onde vejo andamento?</div><div class="faq-item" onclick="app.sugerirResposta('Qual o horário de funcionamento do almoxarifado?')">Horário de funcionamento?</div></div>`; this.renderBottomNav('ouvidoria'); },
      sugerirResposta: function(pergunta) { const respostas={'Como faço para solicitar material?':'Acesse o Catálogo, escolha os itens e finalize.','Onde vejo o andamento do meu pedido?':'Use a opção "Rastrear" no menu.','Qual o horário de funcionamento do almoxarifado?':'Segunda a sexta, 8h às 17h.'}; alert(respostas[pergunta]||'Consulte a equipe.'); },
      sugerirCategoriaManifestacao: function() { const tipo=document.getElementById('manifestacao-tipo').value; const cat=document.getElementById('manifestacao-categoria'); if(tipo==='reclamacao') cat.value='falta_material'; else if(tipo==='sugestao') cat.value='outros'; else if(tipo==='elogio') cat.value='atendimento'; else cat.value='outros'; },
      sugerirFAQ: function(texto) { const div=document.getElementById('faq-sugestoes'); if(texto.toUpperCase().includes('MATERIAL')) div.innerHTML='<p>💡 Dica: Utilize o catálogo.</p>'; else if(texto.toUpperCase().includes('ATRASO')) div.innerHTML='<p>💡 Dica: Informe o código do pedido.</p>'; else div.innerHTML=''; },
      toggleIdentificacao: function() { const anon=document.getElementById('manifestacao-anonimo').checked; const div=document.getElementById('manifestacao-identificacao'); if(anon) { div.style.display='none'; document.getElementById('manifestacao-nome').required=false; document.getElementById('manifestacao-email').required=false; } else { div.style.display='block'; document.getElementById('manifestacao-nome').required=true; document.getElementById('manifestacao-email').required=true; } },
      registrarManifestacao: function() { const tipo=document.getElementById('manifestacao-tipo').value; const categoria=document.getElementById('manifestacao-categoria').value||'outros'; const descricao=document.getElementById('manifestacao-descricao').value.trim(); const anonimo=document.getElementById('manifestacao-anonimo').checked; const nome=anonimo?'Anônimo':document.getElementById('manifestacao-nome').value.trim(); const email=anonimo?null:document.getElementById('manifestacao-email').value.trim(); const arquivo=document.getElementById('manifestacao-anexo').files[0]; if(!tipo||!descricao) { alert('Preencha tipo e descrição.'); return; } if(!anonimo&&(!nome||!email)) { alert('Preencha nome e e-mail ou marque anônimo.'); return; } const codigo='OUV-'+Date.now().toString(36).toUpperCase()+'-'+Math.floor(Math.random()*1000).toString().padStart(3,'0'); const manifestacao={ tipo:"manifestacao", id:Date.now(), codigo, tipo, categoria, descricao, anonimo, nome, email, data:new Date().toISOString(), status:'recebido', historico:[{data:new Date().toISOString(), acao:'Manifestação registrada', status:'recebido'}], anexo:null }; const finalizar=()=>{ this.db.complaints.push(manifestacao); this.saveDatabase(); this.salvarDados('manifestacoes',manifestacao); this.aposRegistrarManifestacao(codigo); }; if(arquivo) { const reader=new FileReader(); reader.onload=e=>{ manifestacao.anexo=e.target.result; finalizar(); }; reader.readAsDataURL(arquivo); } else finalizar(); },
      aposRegistrarManifestacao: function(codigo) { this.closeModal('modal-manifestacao'); document.getElementById('tracking-code-display').innerText=codigo; this.openModal('modal-pedido-realizado'); document.getElementById('form-manifestacao').reset(); document.getElementById('manifestacao-identificacao').style.display='block'; document.getElementById('faq-sugestoes').innerHTML=''; },
      renderMinhasManifestacoes: function() { const content=document.getElementById('main-content'); content.innerHTML=`<h3>📋 Minhas Manifestações</h3><button class="btn-secondary" onclick="app.renderOuvidoriaMenu()">← Voltar</button><div><input type="text" id="filtro-nome-manifestacao" placeholder="Nome ou e-mail" style="width:100%; padding:12px; background:rgba(0,0,0,0.3); border-radius:28px;"><button class="btn-primary" onclick="app.filtrarMinhasManifestacoes()">Buscar</button></div><div id="lista-minhas-manifestacoes"></div>`; this.renderBottomNav('ouvidoria'); },
      filtrarMinhasManifestacoes: function() { const filtro=document.getElementById('filtro-nome-manifestacao').value.toLowerCase(); const container=document.getElementById('lista-minhas-manifestacoes'); if(!filtro) { container.innerHTML='<p>Digite um nome ou e-mail.</p>'; return; } const manifestacoes=this.db.complaints.filter(m=>!m.anonimo&&(m.nome.toLowerCase().includes(filtro)||(m.email&&m.email.toLowerCase().includes(filtro)))).slice().reverse(); if(manifestacoes.length===0) { container.innerHTML='<p>Nenhuma manifestação encontrada.</p>'; return; } let html=''; manifestacoes.forEach(m=>{ let statusClass='status-'+m.status; let statusText=STATUS_MANIFESTACAO[m.status]||m.status; html+=`<div class="item-card"><div><strong>${m.codigo}</strong><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Tipo: ${TIPOS_MANIFESTACAO[m.tipo]||m.tipo}</p><p>Data: ${new Date(m.data).toLocaleDateString()}</p><p>Descrição: ${m.descricao.substring(0,80)}</p><button class="action-btn" onclick="app.acompanharManifestacao(${m.id})">Acompanhar</button></div>`; }); container.innerHTML=html; },
      renderAcompanharManifestacaoPorCodigo: function() { const content=document.getElementById('main-content'); content.innerHTML=`<h3>🔍 Acompanhar por Código</h3><button class="btn-secondary" onclick="app.renderOuvidoriaMenu()">← Voltar</button><div><input type="text" id="codigo-acompanhar" placeholder="Código da manifestação" style="width:100%; padding:12px; background:rgba(0,0,0,0.3); border-radius:28px;"><button class="btn-primary" onclick="app.buscarManifestacaoPorCodigo()">Buscar</button></div><div id="resultado-acompanhar"></div>`; this.renderBottomNav('ouvidoria'); },
      buscarManifestacaoPorCodigo: function() { const codigo=document.getElementById('codigo-acompanhar').value.trim().toUpperCase(); const resultadoDiv=document.getElementById('resultado-acompanhar'); if(!codigo) { resultadoDiv.innerHTML='<p>Digite um código.</p>'; return; } const manifestacao=this.db.complaints.find(m=>m.codigo===codigo); if(!manifestacao) { resultadoDiv.innerHTML='<p>Código não encontrado.</p>'; return; } this.acompanharManifestacao(manifestacao.id,true); },
      acompanharManifestacao: function(id,isPublic=false) { const m=this.db.complaints.find(m=>m.id===id); if(!m) return; this.currentComplaintId=id; const msgs=this.db.complaintMessages.filter(msg=>msg.complaintId===id).sort((a,b)=>new Date(a.data)-new Date(b.data)); const body=document.getElementById('acompanhar-manifestacao-body'); let html=`<p><strong>Código:</strong> ${m.codigo}</p><p><strong>Tipo:</strong> ${TIPOS_MANIFESTACAO[m.tipo]||m.tipo}</p><p><strong>Status:</strong> <span class="tracking-status status-${m.status}">${STATUS_MANIFESTACAO[m.status]||m.status}</span></p><p><strong>Descrição:</strong> ${m.descricao}</p>${m.anexo?`<p><a href="${m.anexo}" target="_blank">📎 Anexo</a></p>`:''}<div class="chat-messages" id="chat-messages-${id}">`; msgs.forEach(msg=>{ const classe=msg.remetente==='usuario'?'user':'admin'; html+=`<div class="chat-message ${classe}"><strong>${msg.remetente==='usuario'?(m.anonimo?'Anônimo':m.nome):'Almoxarifado'}:</strong><p>${msg.texto}</p><small>${new Date(msg.data).toLocaleString()}</small></div>`; }); html+='</div>'; if(m.status!=='concluido') html+=`<div><textarea id="nova-mensagem-${id}" placeholder="Digite sua mensagem..."></textarea><button class="btn-primary" onclick="app.enviarMensagemManifestacao(${id})">Enviar</button></div>`; else { html+='<p>Manifestação concluída.</p>'; if(!m.avaliacao) html+=`<button class="btn-primary" onclick="app.abrirAvaliacao(${id})">⭐ Avaliar atendimento</button>`; } body.innerHTML=html; document.getElementById('acompanhar-manifestacao-footer').innerHTML='<button class="btn-secondary" onclick="app.closeModal(\'modal-acompanhar-manifestacao\')">Fechar</button>'; this.openModal('modal-acompanhar-manifestacao'); },
      enviarMensagemManifestacao: function(id) { const mensagem=document.getElementById(`nova-mensagem-${id}`).value.trim(); if(!mensagem) return; const manifestacao=this.db.complaints.find(m=>m.id===id); if(!manifestacao) return; const msg={id:Date.now(), complaintId:id, remetente:'usuario', texto:mensagem, data:new Date().toISOString()}; this.db.complaintMessages.push(msg); this.saveDatabase(); this.salvarDados('mensagensManifestacao',msg); manifestacao.historico.push({data:msg.data, acao:'Nova mensagem do usuário', status:manifestacao.status}); this.saveDatabase(); this.salvarDados('manifestacoes',manifestacao); this.acompanharManifestacao(id); },
      responderManifestacaoAdmin: function(id) { const mensagem=document.getElementById(`admin-mensagem-${id}`).value.trim(); if(!mensagem) return; const manifestacao=this.db.complaints.find(m=>m.id===id); if(!manifestacao) return; const msg={id:Date.now(), complaintId:id, remetente:'admin', texto:mensagem, data:new Date().toISOString()}; this.db.complaintMessages.push(msg); this.saveDatabase(); this.salvarDados('mensagensManifestacao',msg); manifestacao.historico.push({data:msg.data, acao:'Resposta do almoxarifado', status:manifestacao.status}); this.saveDatabase(); this.salvarDados('manifestacoes',manifestacao); this.abrirAdminManifestacao(id); },
      alterarStatusManifestacao: function(id,novoStatus) { const m=this.db.complaints.find(m=>m.id===id); if(m) { m.status=novoStatus; m.historico.push({data:new Date().toISOString(), acao:`Status alterado para ${STATUS_MANIFESTACAO[novoStatus]}`, status:novoStatus}); this.saveDatabase(); this.salvarDados('manifestacoes',m); } },
      abrirAvaliacao: function(id) { this.currentComplaintId=id; document.querySelectorAll('#rating-stars span').forEach(span=>span.classList.remove('selected')); document.getElementById('avaliacao-comentario').value=''; this.openModal('modal-avaliar-manifestacao'); },
      avaliarManifestacao: function() { const estrelas=document.querySelectorAll('#rating-stars span.selected').length; if(estrelas===0) { alert('Selecione uma avaliação.'); return; } const comentario=document.getElementById('avaliacao-comentario').value.trim(); const manifestacao=this.db.complaints.find(m=>m.id===this.currentComplaintId); if(manifestacao) { manifestacao.avaliacao={estrelas, comentario, data:new Date().toISOString()}; this.saveDatabase(); this.salvarDados('manifestacoes',manifestacao); } this.closeModal('modal-avaliar-manifestacao'); alert('Avaliação registrada!'); if(document.getElementById('modal-acompanhar-manifestacao').classList.contains('active')) this.acompanharManifestacao(this.currentComplaintId); },
      renderAdminOuvidoria: function() { if(!this.isAdmin) return; const content=document.getElementById('main-content'); let html=`<div><h3>📢 Gestão de Ouvidoria</h3><button class="btn-secondary" onclick="app.renderAdminPanel()">← Voltar</button></div><div><h4>Indicadores</h4><div class="dashboard-cards"><div><div>${this.db.complaints.length}</div><div>Total</div></div><div><div>${this.db.complaints.filter(m=>m.status==='recebido').length}</div><div>Recebidos</div></div><div><div>${this.db.complaints.filter(m=>m.status==='analise').length}</div><div>Em análise</div></div><div><div>${this.db.complaints.filter(m=>m.status==='atendimento').length}</div><div>Em atendimento</div></div><div><div>${this.db.complaints.filter(m=>m.status==='concluido').length}</div><div>Concluídos</div></div></div><div><select id="filtro-status-manifestacao" onchange="app.filtrarManifestacoesAdmin()"><option value="">Todos</option><option value="recebido">Recebido</option><option value="analise">Análise</option><option value="atendimento">Atendimento</option><option value="concluido">Concluído</option></select><select id="filtro-tipo-manifestacao" onchange="app.filtrarManifestacoesAdmin()"><option value="">Todos tipos</option><option value="reclamacao">Reclamação</option><option value="sugestao">Sugestão</option><option value="elogio">Elogio</option><option value="duvida">Dúvida</option><option value="denuncia">Denúncia</option></select></div><div id="lista-manifestacoes-admin"></div>`; content.innerHTML=html; this.filtrarManifestacoesAdmin(); this.renderBottomNav('admin'); },
      filtrarManifestacoesAdmin: function() { const statusFiltro=document.getElementById('filtro-status-manifestacao')?.value; const tipoFiltro=document.getElementById('filtro-tipo-manifestacao')?.value; let lista=this.db.complaints.slice().reverse(); if(statusFiltro) lista=lista.filter(m=>m.status===statusFiltro); if(tipoFiltro) lista=lista.filter(m=>m.tipo===tipoFiltro); const container=document.getElementById('lista-manifestacoes-admin'); if(!container) return; if(lista.length===0) { container.innerHTML='<p>Nenhuma manifestação.</p>'; return; } let html=''; lista.forEach(m=>{ let statusClass='status-'+m.status; let statusText=STATUS_MANIFESTACAO[m.status]||m.status; html+=`<div class="item-card"><div><strong>${m.codigo}</strong><span class="tracking-status ${statusClass}">${statusText}</span></div><p>Tipo: ${TIPOS_MANIFESTACAO[m.tipo]||m.tipo}</p><p>Data: ${new Date(m.data).toLocaleString()}</p><p>Solicitante: ${m.anonimo?'Anônimo':m.nome} ${m.email?`(${m.email})`:''}</p><p>Descrição: ${m.descricao.substring(0,80)}</p><div><button class="action-btn" onclick="app.abrirAdminManifestacao(${m.id})">👁️ Ver</button><select onchange="app.alterarStatusManifestacaoAdmin(${m.id}, this.value)"><option value="">Mudar status</option><option value="recebido">Recebido</option><option value="analise">Em análise</option><option value="atendimento">Em atendimento</option><option value="concluido">Concluído</option></select></div></div>`; }); container.innerHTML=html; },
      abrirAdminManifestacao: function(id) { const m=this.db.complaints.find(m=>m.id===id); if(!m) return; this.currentComplaintId=id; const msgs=this.db.complaintMessages.filter(msg=>msg.complaintId===id).sort((a,b)=>new Date(a.data)-new Date(b.data)); const body=document.getElementById('acompanhar-manifestacao-body'); let html=`<p><strong>Código:</strong> ${m.codigo}</p><p><strong>Tipo:</strong> ${TIPOS_MANIFESTACAO[m.tipo]||m.tipo}</p><p><strong>Status:</strong> <span class="tracking-status status-${m.status}">${STATUS_MANIFESTACAO[m.status]||m.status}</span></p><p><strong>Solicitante:</strong> ${m.anonimo?'Anônimo':m.nome} ${m.email?`(${m.email})`:''}</p><p><strong>Descrição:</strong> ${m.descricao}</p>${m.anexo?`<p><a href="${m.anexo}" target="_blank">📎 Anexo</a></p>`:''}<div class="chat-messages" id="chat-messages-${id}">`; msgs.forEach(msg=>{ const classe=msg.remetente==='usuario'?'user':'admin'; html+=`<div class="chat-message ${classe}"><strong>${msg.remetente==='usuario'?(m.anonimo?'Anônimo':m.nome):'Almoxarifado'}:</strong><p>${msg.texto}</p><small>${new Date(msg.data).toLocaleString()}</small></div>`; }); html+=`</div><div><textarea id="admin-mensagem-${id}" placeholder="Digite sua resposta..."></textarea><button class="btn-primary" onclick="app.responderManifestacaoAdmin(${id})">Enviar</button></div>`; body.innerHTML=html; document.getElementById('acompanhar-manifestacao-footer').innerHTML='<button class="btn-secondary" onclick="app.closeModal(\'modal-acompanhar-manifestacao\')">Fechar</button>'; this.openModal('modal-acompanhar-manifestacao'); },
      alterarStatusManifestacaoAdmin: function(id,novoStatus) { if(!novoStatus) return; this.alterarStatusManifestacao(id,novoStatus); this.filtrarManifestacoesAdmin(); },
      renderQRInventory: function() { if(!this.isAdmin) return; const content=document.getElementById('main-content'); content.innerHTML=`<div><h3>📱 Controle QR Code</h3><button class="btn-secondary" onclick="app.renderAdminPanel()">← Voltar</button></div><div><button class="action-btn primary" onclick="app.abrirQRItemForm()">➕ Cadastrar</button><button class="action-btn" onclick="app.abrirQRScanner()">📷 Escanear</button><button class="action-btn" onclick="app.renderQRItemList()">📋 Listar</button></div><div id="qr-inventory-content">${this.renderQRDashboard()}</div>`; this.renderBottomNav('admin'); },
      renderQRDashboard: function() { const totalItems=this.db.qrItems.length; const estoqueBaixo=this.db.qrItems.filter(i=>i.currentQty<=i.minStock).length; const totalEntradas=this.db.qrTransactions.filter(t=>t.type==='entrada').length; const totalSaidas=this.db.qrTransactions.filter(t=>t.type==='saida').length; return `<div class="dashboard-cards"><div><div>${totalItems}</div><div>Itens</div></div><div><div>${estoqueBaixo}</div><div>Estoque baixo</div></div><div><div>${totalEntradas}</div><div>Entradas</div></div><div><div>${totalSaidas}</div><div>Saídas</div></div></div><h4>Últimas movimentações</h4><div>${this.db.qrTransactions.slice().reverse().slice(0,5).map(t=>{const i=this.db.qrItems.find(i=>i.id===t.itemId); return `<div>${new Date(t.date).toLocaleDateString()}: ${t.type==='entrada'?'+':'-'} ${t.qty} - ${i?.name||'?'}</div>`;}).join('')||'<p>Nenhuma</p>'}</div>`; },
      abrirQRItemForm: function(itemId=null) { const title=document.getElementById('modal-qr-item-title'); const idField=document.getElementById('qr-item-id'); const codeField=document.getElementById('qr-item-code'); const nameField=document.getElementById('qr-item-name'); const categoryField=document.getElementById('qr-item-category'); const unitField=document.getElementById('qr-item-unit'); const locationField=document.getElementById('qr-item-location'); const qtyField=document.getElementById('qr-item-qty'); const minStockField=document.getElementById('qr-item-minstock'); const previewGroup=document.getElementById('qr-code-preview-group'); const previewDiv=document.getElementById('qr-code-preview'); if(itemId){ const item=this.db.qrItems.find(i=>i.id===itemId); if(item){ title.innerText='✏️ Editar Item QR'; idField.value=item.id; codeField.value=item.code; nameField.value=item.name; categoryField.value=item.category; unitField.value=item.unit; locationField.value=item.location; qtyField.value=item.currentQty; minStockField.value=item.minStock; if(item.qrCodeData){ previewGroup.style.display='block'; previewDiv.innerHTML=`<img src="${item.qrCodeData}" style="width:150px;">`;} else previewGroup.style.display='none';} } else { title.innerText='➕ Cadastrar Item QR'; idField.value=''; codeField.value=''; nameField.value=''; categoryField.value=''; unitField.value=''; locationField.value=''; qtyField.value='0'; minStockField.value='5'; previewGroup.style.display='none'; } this.openModal('modal-qr-item'); },
      sugerirCodigoQR: function(){ const cat=document.getElementById('qr-item-category').value; if(!cat) return; const prefix=cat; const items=this.db.qrItems.filter(i=>i.code.startsWith(prefix+'-')); let max=0; items.forEach(i=>{ const parts=i.code.split('-'); if(parts.length===2 && !isNaN(parts[1])) max=Math.max(max,parseInt(parts[1])); }); const next=(max+1).toString().padStart(3,'0'); document.getElementById('qr-item-code').value=`${prefix}-${next}`; },
      salvarQRItem: function(){ const id=document.getElementById('qr-item-id').value; let code=document.getElementById('qr-item-code').value.trim(); const name=document.getElementById('qr-item-name').value.trim(); const category=document.getElementById('qr-item-category').value; const unit=document.getElementById('qr-item-unit').value.trim(); const location=document.getElementById('qr-item-location').value.trim(); const qty=parseInt(document.getElementById('qr-item-qty').value)||0; const minStock=parseInt(document.getElementById('qr-item-minstock').value)||5; if(!name||!category||!unit||!location){ alert('Preencha todos os campos'); return; } let finalCode=code; if(!finalCode){ const prefix=category; const items=this.db.qrItems.filter(i=>i.code.startsWith(prefix+'-')); let max=0; items.forEach(i=>{ const parts=i.code.split('-'); if(parts.length===2 && !isNaN(parts[1])) max=Math.max(max,parseInt(parts[1])); }); finalCode=`${prefix}-${(max+1).toString().padStart(3,'0')}`; } const qrData=this.generateQRCode(finalCode); const item={ id:id?parseInt(id):Date.now(), code:finalCode, name, category, unit, location, currentQty:qty, minStock, qrCodeData:qrData, createdAt:new Date().toISOString(), updatedAt:new Date().toISOString() }; if(id){ const idx=this.db.qrItems.findIndex(i=>i.id===parseInt(id)); if(idx!==-1){ item.createdAt=this.db.qrItems[idx].createdAt; this.db.qrItems[idx]=item; } } else this.db.qrItems.push(item); this.saveDatabase(); this.salvarDados('itemsQR',item); this.closeModal('modal-qr-item'); this.renderQRInventory(); alert('Item salvo!'); },
      generateQRCode: function(text){ const qrcode = qrcode(0, 'M'); qrcode.addData(text); qrcode.make(); const imgData=qrcode.createImgTag(4); const match=imgData.match(/src="([^"]+)"/); return match?match[1]:""; },
      renderQRItemList: function(){ const div=document.getElementById('qr-inventory-content'); if(!div){ this.renderQRInventory(); setTimeout(()=>this.renderQRItemList(),100); return; } let html='<h4>📦 Itens cadastrados</h4>'; if(this.db.qrItems.length===0) html+='<p>Nenhum item.</p>'; else this.db.qrItems.forEach(item=>{ const low=item.currentQty<=item.minStock; html+=`<div class="qr-item-card" onclick="app.abrirQRItemDetail(${item.id})"><img src="${item.qrCodeData}" style="width:80px;"><div><h4>${item.name} (${item.code})</h4><p>Estoque: ${item.currentQty} ${item.unit} ${low?'<span>Baixo</span>':''}</p><p>Local: ${item.location}</p></div><button onclick="event.stopPropagation(); app.abrirQRItemForm(${item.id})">✏️</button></div>`; }); div.innerHTML=html; },
      abrirQRItemDetail: function(itemId){ const item=this.db.qrItems.find(i=>i.id===itemId); if(!item) return; const div=document.getElementById('qr-inventory-content'); const transactions=this.db.qrTransactions.filter(t=>t.itemId===itemId).slice().reverse(); let html=`<button class="btn-secondary" onclick="app.renderQRInventory()">← Voltar</button><div><img src="${item.qrCodeData}" style="width:150px;"><div><h3>${item.name}</h3><p>Código: ${item.code}</p><p>Categoria: ${item.category}</p><p>Localização: ${item.location}</p><p>Estoque: ${item.currentQty} ${item.unit}</p><p>Mínimo: ${item.minStock}</p><div><button class="btn-primary" onclick="app.abrirEntradaQR(${item.id})">➕ Entrada</button><button class="btn-primary" onclick="app.abrirSaidaQR(${item.id})" ${item.currentQty===0?'disabled':''}>➖ Saída</button><button class="btn-secondary" onclick="window.print()">🖨️ Imprimir</button></div></div></div><h4>Histórico</h4><div>${transactions.length?transactions.map(t=>`<div>${new Date(t.date).toLocaleString()}: ${t.type==='entrada'?'Entrada':'Saída'} de ${t.qty} ${item.unit} ${t.supplier||t.sector||''}</div>`).join(''):'<p>Nenhuma movimentação.</p>'}</div>`; div.innerHTML=html; },
      abrirEntradaQR: function(itemId){ const item=this.db.qrItems.find(i=>i.id===itemId); if(!item) return; document.getElementById('entry-item-id').value=itemId; document.getElementById('entry-item-name').innerText=item.name; document.getElementById('entry-qty').value=1; document.getElementById('entry-date').value=new Date().toISOString().split('T')[0]; document.getElementById('entry-supplier').value=''; this.openModal('modal-qr-entry'); },
      abrirSaidaQR: function(itemId){ const item=this.db.qrItems.find(i=>i.id===itemId); if(!item) return; document.getElementById('exit-item-id').value=itemId; document.getElementById('exit-item-name').innerText=item.name; document.getElementById('exit-qty').value=1; document.getElementById('exit-date').value=new Date().toISOString().split('T')[0]; document.getElementById('exit-sector').value=''; this.openModal('modal-qr-exit'); },
      confirmarEntrada: function(){ const itemId=parseInt(document.getElementById('entry-item-id').value); const qty=parseInt(document.getElementById('entry-qty').value); const date=document.getElementById('entry-date').value; const supplier=document.getElementById('entry-supplier').value.trim(); if(!qty||qty<=0){ alert('Quantidade inválida'); return; } const item=this.db.qrItems.find(i=>i.id===itemId); if(!item) return; const old=item.currentQty; item.currentQty+=qty; item.updatedAt=new Date().toISOString(); const trans={id:Date.now(), itemId, type:'entrada', qty, date, supplier, previousQty:old, newQty:item.currentQty, user:this.currentUser?.name||'Admin'}; this.db.qrTransactions.push(trans); this.saveDatabase(); this.salvarDados('movimentacoesQR',trans); this.salvarDados('itemsQR',item); this.closeModal('modal-qr-entry'); this.abrirQRItemDetail(itemId); this.showNotification('Entrada registrada!'); },
      confirmarSaida: function(){ const itemId=parseInt(document.getElementById('exit-item-id').value); const qty=parseInt(document.getElementById('exit-qty').value); const date=document.getElementById('exit-date').value; const sector=document.getElementById('exit-sector').value.trim(); if(!qty||qty<=0){ alert('Quantidade inválida'); return; } const item=this.db.qrItems.find(i=>i.id===itemId); if(!item) return; if(item.currentQty<qty){ alert('Estoque insuficiente'); return; } const old=item.currentQty; item.currentQty-=qty; item.updatedAt=new Date().toISOString(); const trans={id:Date.now(), itemId, type:'saida', qty, date, sector, previousQty:old, newQty:item.currentQty, user:this.currentUser?.name||'Admin'}; this.db.qrTransactions.push(trans); this.saveDatabase(); this.salvarDados('movimentacoesQR',trans); this.salvarDados('itemsQR',item); this.closeModal('modal-qr-exit'); this.abrirQRItemDetail(itemId); this.showNotification('Saída registrada!'); },
      abrirQRScanner: function(){ this.openModal('modal-qr-scanner'); if(!this.html5QrCode) this.html5QrCode=new Html5Qrcode("qr-reader"); const success=(decodedText)=>{ this.html5QrCode.stop().then(()=>{ this.closeModal('modal-qr-scanner'); this.processQRScan(decodedText); }).catch(err=>alert(err)); }; const config={fps:10,qrbox:{width:250,height:250}}; this.html5QrCode.start({facingMode:"environment"},config,success,()=>{}).catch(err=>alert('Erro câmera: '+err)); },
      closeQRScanner: function(){ if(this.html5QrCode) this.html5QrCode.stop().then(()=>this.closeModal('modal-qr-scanner')).catch(()=>this.closeModal('modal-qr-scanner')); else this.closeModal('modal-qr-scanner'); },
      processQRScan: function(code){ const item=this.db.qrItems.find(i=>i.code===code); if(item){ this.renderQRInventory(); setTimeout(()=>this.abrirQRItemDetail(item.id),100); } else { if(confirm(`Código "${code}" não encontrado. Deseja cadastrar novo item?`)){ this.abrirQRItemForm(); document.getElementById('qr-item-code').value=code; } } },
      renderFilaPublica: function(){ const content=document.getElementById('main-content'); const solicitacoes=[...this.db.waterRequests].sort((a,b)=>new Date(a.data)-new Date(b.data)); let html=`<div data-screen="fila"><h2>🚰 Fila de Solicitações de Água</h2><div><button class="btn-secondary" onclick="app.atualizarFilaManual()">🔄 Atualizar</button></div><div id="fila-lista">`; if(solicitacoes.length===0) html+='<p>Nenhuma solicitação.</p>'; else{ html+='<ul>'; solicitacoes.forEach((s,idx)=>{ let statusClass='',statusText=s.status; switch(s.status){ case'pendente': statusClass='status-pendente'; statusText='Pendente'; break; case'aprovado': statusClass='status-aprovado'; statusText='Aprovado'; break; case'entregue': statusClass='status-entregue'; statusText='Entregue'; break; case'confirmado': statusClass='status-confirmado'; statusText='Confirmado'; break; case'negado': statusClass='status-negado'; statusText='Negado'; break; case'aguardando_reposicao': statusClass='status-aguardando'; statusText='Aguardando Reposição'; break; default: statusClass='status-analise'; } const mostraPos=(s.status==='pendente'||s.status==='aguardando_reposicao'); const pos=mostraPos?`<span>#${idx+1}</span>`:''; html+=`<li class="item-card"><div><strong>${s.codigo}</strong>${pos}<span class="tracking-status ${statusClass}">${statusText.toUpperCase()}</span></div><p>Solicitante: ${s.nome}</p><p>Data: ${new Date(s.data).toLocaleString()}</p><p>Local: ${s.local}</p><p>Quantidade: ${s.quantidade}</p></li>`; }); html+='</ul>'; } html+=`</div></div>`; content.innerHTML=html; this.renderBottomNav('fila'); },
      atualizarFilaManual: function(){ this.renderFilaPublica(); this.showNotification('Lista atualizada!'); },
      openAdminLogin: function(){ document.getElementById('admin-email').value='almoxarifadoCT'; document.getElementById('admin-password').value=''; this.openModal('modal-admin-login'); },
      adminLogin: function(){ const email=document.getElementById('admin-email').value.trim(); const pass=document.getElementById('admin-password').value; const user=this.db.users.find(u=>u.email===email&&u.password===btoa(pass)&&(u.role==='admin'||u.role==='entregador')); if(user){ this.currentUser=user; this.isAdmin=user.role==='admin'; this.isEntregador=user.role==='entregador'; sessionStorage.setItem('adminUser',JSON.stringify(user)); document.getElementById('user-greeting').innerText=`${user.role.toUpperCase()}: ${user.name}`; this.closeModal('modal-admin-login'); if(this.isAdmin){ this.renderAdminPanel(); this.renderBottomNav('admin'); } else { this.abrirGerenciarSolicitacoesAgua(); this.renderBottomNav('entregas'); } this.updateAdminButtonIcon(); } else alert('Credenciais inválidas.'); },
      logoutAdmin: function(){ this.currentUser=null; this.isAdmin=false; this.isEntregador=false; sessionStorage.removeItem('adminUser'); document.getElementById('user-greeting').innerText='Solicitar Água Mineral'; this.renderCatalog(); this.renderBottomNav('catalog'); this.updateAdminButtonIcon(); },
      toggleAdmin: function(){ if(this.isAdmin||this.isEntregador) this.logoutAdmin(); else this.openAdminLogin(); },
      updateAdminButtonIcon: function(){ const btn=document.getElementById('admin-login-btn'); btn.innerHTML='<span style="font-size:1.5rem;">👤</span>'; },
      renderBottomNav: function(active){ const nav=document.getElementById('bottom-nav'); let html=''; if(this.isAdmin){ html=`<button class="nav-item ${active==='catalog'?'active':''}" onclick="app.renderCatalog()"><span>📦</span><span>Catálogo</span></button><button class="nav-item ${active==='agua'?'active':''}" onclick="app.renderSolicitarAgua()"><span>💧</span><span>Água</span></button><button class="nav-item ${active==='track'?'active':''}" onclick="app.renderTrackOrder()"><span>🔍</span><span>Rastrear</span></button><button class="nav-item ${active==='admin'?'active':''}" onclick="app.renderAdminPanel()"><span>⚙️</span><span>Admin</span></button>`; } else if(this.isEntregador){ html=`<button class="nav-item ${active==='catalog'?'active':''}" onclick="app.renderCatalog()"><span>📦</span><span>Catálogo</span></button><button class="nav-item ${active==='entregas'?'active':''}" onclick="app.abrirGerenciarSolicitacoesAgua()"><span>💧</span><span>Entregas</span></button><button class="nav-item ${active==='track'?'active':''}" onclick="app.renderTrackOrder()"><span>🔍</span><span>Rastrear</span></button>`; } else { html=`<button class="nav-item ${active==='catalog'?'active':''}" onclick="app.renderCatalog()"><span>📦</span><span>Catálogo</span></button><button class="nav-item ${active==='agua'?'active':''}" onclick="app.renderSolicitarAgua()"><span>💧</span><span>Água</span></button><button class="nav-item ${active==='minhas-solicitacoes'?'active':''}" onclick="app.renderMinhasSolicitacoesAgua()"><span>📋</span><span>Minhas Solic.</span></button><button class="nav-item ${active==='fila'?'active':''}" onclick="app.renderFilaPublica()"><span>🚰</span><span>Fila</span></button><button class="nav-item ${active==='track'?'active':''}" onclick="app.renderTrackOrder()"><span>🔍</span><span>Rastrear</span></button><button class="nav-item ${active==='ouvidoria'?'active':''}" onclick="app.renderOuvidoriaMenu()"><span>📢</span><span>Ouvidoria</span></button>`; } nav.innerHTML=html; },
      openModal: function(id){ document.getElementById(id).classList.add('active'); },
      closeModal: function(id){ document.getElementById(id).classList.remove('active'); },
      setupEventListeners: function(){ document.querySelectorAll('.modal-overlay').forEach(modal=>{ modal.addEventListener('click',function(e){ if(e.target===this) this.classList.remove('active'); }); }); document.addEventListener('click',function(e){ if(e.target.matches('#rating-stars span')){ const stars=document.querySelectorAll('#rating-stars span'); stars.forEach(s=>s.classList.remove('selected')); let val=e.target.getAttribute('data-value'); for(let i=0;i<val;i++) stars[i].classList.add('selected'); } }); }
    };

    app.init();
  </script>
</body>
</html>
