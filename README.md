# Ramsons Metas — App Android Nativo

App de acompanhamento de metas de vendas para a equipe Ramsons.  
Desenvolvido em **Kotlin nativo** com **Room Database (SQLite)**.

---

## 📱 Telas do app

| Tela | Descrição |
|---|---|
| **Dashboard** | Cards de todas as 6 metas com progresso, badge de status e resumo do mês |
| **Lançar Venda** | Formulário para registrar vendas por categoria |
| **Histórico** | Lista de todas as vendas do mês com opção de deletar |
| **Metas / Config** | Definir metas mensais e dias úteis |

## 🗂 Categorias

- 🛍️ Produtos Vendidos (R$)
- 🛡️ Garantia Estendida (R$)
- 🔒 Seguro (R$)
- 💻 PSD — Informática (R$)
- 💳 Crediário UME (R$)
- ❄️ Instalação de Ar-condicionado (quantidade)

---

## 🛠 Stack Tecnológica

- **Linguagem:** Kotlin
- **Banco de dados:** Room (SQLite) — persistência local
- **Arquitetura:** MVVM (ViewModel + LiveData)
- **Navegação:** Navigation Component + Bottom Navigation
- **UI:** ViewBinding, RecyclerView, Material Components
- **Coroutines:** para operações assíncronas no banco

---

## 🚀 Como abrir e compilar no Android Studio

### Pré-requisitos
- **Android Studio Hedgehog** (2023.1.1) ou mais recente
- **JDK 17** (incluído no Android Studio)
- **Android SDK** com API 26+ instalada

### Passos

1. **Extraia o ZIP** em uma pasta de sua escolha

2. **Abra o Android Studio**

3. Vá em **File → Open** e selecione a pasta `RamsonsMetas`

4. Aguarde o **Gradle Sync** terminar (pode levar alguns minutos na primeira vez)

5. Conecte um celular Android (com USB Debugging ativado) **ou** use o emulador

6. Clique em **▶ Run** (ou `Shift+F10`)

### Gerar APK para instalar

1. No Android Studio: **Build → Build Bundle(s) / APK(s) → Build APK(s)**
2. O APK estará em: `app/build/outputs/apk/debug/app-debug.apk`
3. Transfira o `.apk` para o celular e instale
   - O celular precisa ter **"Instalar apps desconhecidos"** habilitado

---

## 📁 Estrutura do Projeto

```
app/src/main/
├── java/com/ramsons/metas/
│   ├── MainActivity.kt
│   ├── data/
│   │   ├── dao/          (VendaDao, MetaDao, ConfigDao)
│   │   ├── database/     (AppDatabase - Room)
│   │   └── entity/       (Venda, Meta, Config)
│   ├── ui/
│   │   ├── dashboard/    (DashboardFragment + ViewModel + Adapter)
│   │   ├── lancar/       (LancarFragment + ViewModel)
│   │   ├── historico/    (HistoricoFragment + ViewModel + Adapter)
│   │   └── config/       (ConfigFragment + ViewModel)
│   └── util/
│       ├── Categorias.kt
│       └── FormatUtils.kt
└── res/
    ├── layout/           (XMLs de todas as telas)
    ├── navigation/       (nav_graph.xml)
    ├── menu/             (bottom_nav_menu.xml)
    ├── drawable/         (backgrounds, badges, botões)
    └── values/           (colors, strings, themes)
```

---

## 🗄 Banco de Dados (Room)

Tabelas criadas automaticamente no primeiro uso:

| Tabela | Campos |
|---|---|
| `vendas` | id, categoria, cliente, valor, data, mes |
| `metas` | categoria (PK), valorMeta |
| `config` | chave (PK), valor |

Os dados ficam salvos localmente no dispositivo, sem necessidade de internet.

---

## 🎨 Tema

Dark theme fiel ao app web original:
- Fundo: `#0F1117`
- Cards: `#1A1D27`
- Accent: `#4F6EF7`
- Verde / Amarelo / Vermelho para status das metas
