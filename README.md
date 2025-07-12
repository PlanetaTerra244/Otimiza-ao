-- CONFIG OTIMIZAÇÃO
local ToDisable = {
	Textures = true,
	VisualEffects = true,
	Parts = true,
	Particles = true,
	Sky = true
}
local Stuff = {}

for _, v in next, game:GetDescendants() do
	if ToDisable.Parts and (v:IsA("Part") or v:IsA("UnionOperation") or v:IsA("BasePart")) then
		v.Material = Enum.Material.SmoothPlastic
		table.insert(Stuff, v)
	end
	if ToDisable.Particles and (v:IsA("ParticleEmitter") or v:IsA("Smoke") or v:IsA("Explosion") or v:IsA("Sparkles") or v:IsA("Fire")) then
		v.Enabled = false
		table.insert(Stuff, v)
	end
	if ToDisable.VisualEffects and (v:IsA("BloomEffect") or v:IsA("BlurEffect") or v:IsA("DepthOfFieldEffect") or v:IsA("SunRaysEffect")) then
		v.Enabled = false
		table.insert(Stuff, v)
	end
	if ToDisable.Textures and (v:IsA("Decal") or v:IsA("Texture")) then
		v.Texture = ""
		table.insert(Stuff, v)
	end
	if ToDisable.Sky and v:IsA("Sky") then
		v.Parent = nil
		table.insert(Stuff, v)
	end
end
