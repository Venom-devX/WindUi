# 🌬️ WindUI Library - Documentação

Biblioteca moderna e otimizada para criação de interfaces no Roblox.

---

## 🛠️ Inicialização
Este comando carrega a biblioteca diretamente do repositório oficial.
```lua
local WindUI = loadstring(game:HttpGet("https://raw.githubusercontent.com/Venom-devX/WindUi/main/main.lua"))()
```
---

## 🖼️ Janela Principal (Window)
A base da sua interface. Aqui você define o título, tema e configurações de salvamento.
```lua
local Window = WindUI:CreateWindow({
    Title = "WindUI Library",
    Icon = "rbxassetid://129260712070622",
    Author = "Seu Nome",
    Folder = "WindUI_Configs", -- Nome da pasta onde as configs serão salvas
    Size = UDim2.fromOffset(580, 460),
    Transparent = true,
    Theme = "Dark", -- "Dark" ou "Light"
    KeySystem = { -- Opcional: Remova se não quiser sistema de chave
        Key = { "123", "456" },
        Note = "A chave é 123",
        SaveKey = true
    }
})
```
---

## 📂 Organização (Sections & Tabs)
As **Sections** agrupam as **Tabs** na barra lateral.

### Criar uma Seção:
```lua
local MinhaSecao = Window:Section({
    Title = "Categoria Exemplo",
    Opened = true -- Define se a seção começa aberta
})
```
### Criar uma Aba:
```lua
local MinhaAba = MinhaSecao:Tab({ 
    Title = "Início", 
    Icon = "house", 
    Desc = "Descrição da aba" 
})
```
---

## 🧩 Elementos de Interface

### 🔘 Botão (Button)
```lua
Executa uma função ao ser clicado.
MinhaAba:Button({
    Title = "Clique Aqui",
    Desc = "Executa uma ação no console",
    Callback = function()
        print("Botão clicado!")
    end
})
```
### 🔘 Toggle (Interruptor)
Alterna entre verdadeiro (true) e falso (false).
```lua
MinhaAba:Toggle({
    Title = "Ativar Feature",
    Value = false, -- Valor inicial
    Callback = function(state)
        print("Status: ", state)
    end
})
```
### 🛝 Slider (Deslizante)
Ajusta valores numéricos dentro de um intervalo.
```lua
MinhaAba:Slider({
    Title = "Velocidade",
    Value = { Min = 16, Max = 100, Default = 16 },
    Step = 1,
    Callback = function(v)
        print("Valor: ", v)
    end
})
```
### 🔽 Dropdown (Lista)
Permite selecionar uma ou várias opções.
```lua
MinhaAba:Dropdown({
    Title = "Selecionar Opção",
    Values = { "Opção 1", "Opção 2", "Opção 3" },
    Multi = false, -- Se true, permite selecionar vários
    Callback = function(v)
        print("Selecionado: ", v)
    end
})
```
### ⌨️ Input (Entrada de Texto)
```lua
Caixa para digitação do usuário.
MinhaAba:Input({
    Title = "Digite algo",
    Placeholder = "Escreva aqui...",
    Callback = function(text)
        print("Digitado: ", text)
    end
})
```
### 🎨 ColorPicker (Seletor de Cor)
```lua
MinhaAba:Colorpicker({
    Title = "Cor da UI",
    Default = Color3.fromRGB(255, 0, 0),
    Callback = function(color)
        print("Cor: ", color)
    end
})
```
### ⌨️ Keybind (Atalho)
```lua
MinhaAba:Keybind({
    Title = "Atalho",
    Value = "F",
    Callback = function()
        print("Tecla pressionada!")
    end
})
```
---

## 📢 Notificações e Popups

### Notificação:
```lua
WindUI:Notify({
    Title = "Aviso",
    Content = "Script carregado com sucesso!",
    Duration = 5,
    Icon = "check"
})
```

### Popup (Janela de Confirmação):
```lua
WindUI:Popup({
    Title = "Atenção",
    Content = "Deseja continuar?",
    Buttons = {
        { Title = "Sim", Variant = "Primary", Callback = function() print("Sim") end },
        { Title = "Não", Variant = "Secondary", Callback = function() print("Não") end }
    }
})
```
---

## 💾 Sistema de Configurações (ConfigManager)
Permite salvar e carregar as preferências do usuário.
```lua
local ConfigManager = Window.ConfigManager
local myConfig = ConfigManager:CreateConfig("minha_config")

-- Registre os elementos que deseja salvar:
myConfig:Register("MeuToggle", elemento_toggle)
myConfig:Register("MeuSlider", elemento_slider)

-- Para Salvar/Carregar:
myConfig:Save()
myConfig:Load()
```
