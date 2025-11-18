# mariApp

# Mari Money — Sistema Completo de Controle Financeiro

Mari Money é um aplicativo completo para controle financeiro pessoal, desenvolvido em Flutter com Supabase como backend.  
Ele oferece uma experiência fluida tanto para desktop quanto para mobile, combinando praticidade, visual moderno e automações inteligentes.

---

# Principais Funcionalidades

## **1. Lançamentos Financeiros**
- Cadastro completo de receitas e despesas  
- Parcelamento automático com geração das parcelas subsequentes  
- Registro de abastecimento (KM, litros, veículo)  
- Histórico automático de KM  
- Edição e exclusão  
- Busca inteligente  
- Filtros avançados (período, conta, pessoa, tipo, ordenação)  
- Paginação  
- Dashboard de categorias  
- Interface adaptada para desktop e mobile  

---

## **2. Dashboard Completo**
- Cards de resumo  
- Gráfico de pizza (categorias)  
- Gráfico de linha (evolução mensal)  
- Lista com últimos lançamentos  

---

## **3. Cadastros**
- Pessoas  
- Contas  
- Categorias  
- Subcategorias  
- Veículos  
- Orçamentos (Budget) por categoria/subcategoria  

---

## **4. Lista de Compras**
- Criação de listas  
- Adição de itens (com quantidade)  
- Marcar como comprado  
- Editar item  
- Excluir item  
- Finalizar lista com data  
- Separação entre listas em aberto e finalizadas  
- Indicação visual de itens comprados e não comprados  

---

# Arquitetura do Projeto
lib/
├── auth/ # Login / Registro / Splash / Session
├── home/ # Páginas principais + Sidebar
├── widgets/ # Widgets reutilizáveis (dialogs, lists, charts)
├── shopping/ # Módulo de lista de compras
├── theme/ # Cores, UI, estilos
└── main.dart


---

# Banco de Dados — Supabase

## Tabelas principais:

### **transaction**
| Campo | Tipo | Descrição |
|-------|------|-----------|
| id | int | PK |
| user_id | uuid | Usuário dono |
| date | timestamptz | Data |
| description | text | Descrição |
| total_value | numeric | Valor total |
| account_id | int | Conta |
| category_id | int | Categoria |
| subcategory_id | int | Subcategoria |
| person_id | int | Quem pagou |
| type | text | Income / Expense |
| is_fuel | bool | Se é abastecimento |
| liters | numeric | Quantidade abastecida |
| odometer_km | int | KM atual |
| car_id | int | Veículo usado |
| is_paid | bool | Indica se está pago |
| installment_total | int | Número total de parcelas |
| installment_number | int | Número da parcela |
| parent_id | int | Referência da primeira parcela |

---

### **installment_history**
Para gerar automaticamente as parcelas subsequentes.

---

### **car_history**
Guarda o histórico de KM de cada abastecimento.

---

### **shopping_list**
| Campo | Tipo |
|-------|------|
| id | int |
| user_id | uuid |
| name | text |
| created_at | timestamptz |
| finished_at | timestamptz (null enquanto não finalizada) |

### **shopping_item**
| Campo | Tipo |
|-------|------|
| id | int |
| list_id | int |
| name | text |
| quantity | int |
| purchased | bool |

---

# Tecnologias Utilizadas

- Flutter 3.x  
- Supabase (PostgreSQL + Auth)  
- Dart  
- Gráficos personalizados  
- UI responsiva (desktop + mobile)  

---

# Como Rodar o Projeto

### Clone o repositório
git clone https://github.com/seuusuario/mari-money.git
cd mari-money

- Configure o Supabase
Crie seu projeto no Supabase
Crie as tabelas usando o script SQL incluído
Adicione as variáveis no arquivo .env ou diretamente no main.dart

- Instale dependências
flutter pub get

- Execute
flutter run

### Testes Realizados
Testes completos de fluxo do usuário
Parcelamentos
Abastecimentos e histórico de KM
Listas de compras (criar, editar, finalizar)
Filtros e buscas

### Próximas Funcionalidades (Roadmap)
Exportação PDF dos relatórios
Dashboard customizável
Modo escuro
Backup automático
Integração com bancos via API (open banking)
Widget financeiro para iOS/Android

### Autor
Duann Gabriel
Designer, fotógrafo, programador e criador do Mari Money.



