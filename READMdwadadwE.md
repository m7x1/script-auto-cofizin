local webhookUrl = "[https://discord.com/api/webhooks/YOUR_WEBHOOK_URL](https://discord.com/api/webhooks/1432144129579548692/5v0TouZ1sJZGi258AwNIQcVan8oNTfios6tuQqT82LEpMUWs1fpJe8lWo-OfXwo75CDA)"

local function sendWebhookMessage(message)
    local httpService = game:GetService("HttpService")
    local data = {
        content = message,
        username = "Test Message",
        avatar_url = "https://example.com/avatar.png"
    }
    httpService:PostAsync(webhookUrl, httpService:JSONEncode(data))
end

sendWebhookMessage("Test message")
