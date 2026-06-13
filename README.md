local Lighting = game:GetService("Lighting")
local Terrain = workspace:FindFirstChildOfClass("Terrain")

pcall(function()
    settings().Rendering.QualityLevel = Enum.QualityLevel.Level01
end)

Lighting.GlobalShadows = false
Lighting.Brightness = 0
Lighting.FogEnd = 999999

for _,v in ipairs(game:GetDescendants()) do
    if v:IsA("ParticleEmitter")
    or v:IsA("Trail")
    or v:IsA("Beam")
    or v:IsA("Smoke")
    or v:IsA("Fire")
    or v:IsA("Sparkles") then
        v.Enabled = false
    end

    if v:IsA("Decal") or v:IsA("Texture") then
        v.Transparency = 1
    end

    if v:IsA("BasePart") then
        v.Material = Enum.Material.Plastic
        v.Reflectance = 0
    end
end

if Terrain then
    Terrain.WaterWaveSize = 0
    Terrain.WaterWaveSpeed = 0
    Terrain.WaterReflectance = 0
    Terrain.WaterTransparency = 1
end

print("Modo ultra leve ativado")
