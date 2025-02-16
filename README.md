if not game:IsLoaded() then
    game.Loaded:Wait()
end

local lib = loadstring(game:HttpGet("URL_DA_SUA_LIB"))()
local Window = lib:CreateWindow("Meu Script")

-- Adicione aqui as abas e seções conforme necessário
