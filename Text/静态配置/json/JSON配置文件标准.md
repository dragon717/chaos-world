# 混沌世界 - JSON配置文件标准格式参考

> **目标**：为C#和Go开发者提供标准化的JSON配置文件格式，确保静态配置数据的一致性和可读性

## 📋 总体设计原则

### 命名规范
- **文件命名**：使用PascalCase，如 `RegionConfig.json`、`ItemConfig.json`
- **字段命名**：使用PascalCase，便于C#直接映射，Go可通过tag转换
- **枚举值**：使用PascalCase，如 `"Quality": "MasterWork"`
- **ID标识**：统一使用字符串格式，便于扩展和维护

### 数据类型约定
```json
{
  "StringField": "文本内容",
  "IntField": 100,
  "FloatField": 1.5,
  "BoolField": true,
  "ArrayField": ["item1", "item2"],
  "ObjectField": {
    "SubField": "value"
  }
}
```

### 通用字段结构
```json
{
  "ID": "唯一标识符",
  "Name": "显示名称",
  "Description": "详细描述",
  "Version": "1.0.0",
  "LastModified": "2024-01-01T00:00:00Z"
}
```

---

## 🗺️ 地域配置 (RegionConfig.json)

### 数据结构
```json
{
  "Version": "1.0.0",
  "LastModified": "2024-01-01T00:00:00Z",
  "Regions": [
    {
      "RegionID": "CentralPlains",
      "Name": "中原农桑之地",
      "DisplayName": "中原农桑之地",
      "Description": "大河滋养的肥沃平原，稻田桑园遍布，村镇星罗棋布",
      "RegionType": "Agricultural",
      "Climate": {
        "Type": "Temperate",
        "Temperature": {
          "Spring": 18,
          "Summer": 28,
          "Autumn": 20,
          "Winter": 5
        },
        "Rainfall": {
          "Spring": 120,
          "Summer": 180,
          "Autumn": 100,
          "Winter": 40
        },
        "Disasters": ["Flood", "Drought"]
      },
      "Terrain": {
        "Primary": "Plains",
        "Secondary": ["River", "Hills"],
        "Elevation": {
          "Min": 0,
          "Max": 200,
          "Average": 50
        }
      },
      "Resources": {
        "Primary": ["Rice", "Silk", "Clay"],
        "Secondary": ["Bamboo", "FreshwaterFish"],
        "Rare": ["Jade", "GoldSand"]
      },
      "Population": {
        "Total": 25000000,
        "Density": "High",
        "MainTribes": ["HanMajority", "HakkaMinority"]
      },
      "Culture": {
        "Dominant": "Confucian",
        "Traditions": ["PoetryGathering", "ClanRitual", "MidAutumnFestival"],
        "Values": ["Education", "Harmony", "Tradition"]
      },
      "Economy": {
        "Primary": "Agriculture",
        "Secondary": ["Handicraft", "Trade"],
        "TradeRoutes": ["GrandCanal", "SilkRoad"]
      },
      "Modifiers": {
        "CropYield": 1.2,
        "CraftQuality": 1.1,
        "CulturalInfluence": 1.3,
        "TechProgress": 1.0
      },
      "SeasonalEffects": {
        "Spring": {
          "PlantGrowth": 1.2,
          "CultivationBonus": 0.15
        },
        "Summer": {
          "HarvestYield": 1.1,
          "DisasterRisk": 1.3
        },
        "Autumn": {
          "HarvestYield": 1.3,
          "CulturalActivity": 1.2
        },
        "Winter": {
          "CraftActivity": 1.1,
          "StudyBonus": 1.15
        }
      }
    }
  ]
}
```

### 枚举定义
```json
{
  "RegionTypes": [
    "Agricultural", "Maritime", "Nomadic", "Forest", "Desert", "Mountain"
  ],
  "ClimateTypes": [
    "Temperate", "Tropical", "Arid", "Continental", "Polar"
  ],
  "TerrainTypes": [
    "Plains", "Hills", "Mountains", "River", "Lake", "Coast", "Forest", "Desert", "Swamp"
  ]
}
```

---

## 🎒 物品配置 (ItemConfig.json)

### 数据结构
```json
{
  "Version": "1.0.0",
  "LastModified": "2024-01-01T00:00:00Z",
  "Items": [
    {
      "ItemID": "IronOre",
      "Name": "铁矿石",
      "DisplayName": "铁矿石",
      "Description": "基础冶炼材料，分布于高山岭脊地区",
      "Category": "Mineral",
      "SubCategory": "MetalOre",
      "Quality": {
        "Base": "Common",
        "Possible": ["Poor", "Common", "Fine", "Superior"]
      },
      "Rarity": "Common",
      "Properties": {
        "Weight": 2.5,
        "Volume": 1.0,
        "Durability": 100,
        "StackSize": 50,
        "BasePrice": 10
      },
      "Attributes": {
        "Hardness": 6,
        "Purity": 0.7,
        "MeltingPoint": 1538
      },
      "ObtainMethods": [
        {
          "Method": "Mining",
          "Location": ["HighMountains", "HillsideCliffs"],
          "Difficulty": "Easy",
          "RequiredTools": ["Pickaxe"],
          "RequiredSkills": {
            "Mining": 1
          },
          "YieldRange": {
            "Min": 1,
            "Max": 5,
            "Average": 2.5
          }
        }
      ],
      "Usage": {
        "CraftingMaterial": true,
        "Consumable": false,
        "Equipment": false,
        "TradeGood": true
      },
      "CraftingRecipes": [
        {
          "ResultItem": "IronIngot",
          "RequiredAmount": 3,
          "RequiredFacility": "Furnace",
          "RequiredSkill": {
            "Smelting": 2
          }
        }
      ],
      "RegionalModifiers": {
        "HighMountains": {
          "QualityBonus": 0.2,
          "YieldBonus": 0.1
        },
        "HillsideCliffs": {
          "QualityBonus": 0.1,
          "YieldBonus": 0.15
        }
      },
      "SeasonalModifiers": {
        "Spring": {
          "AvailabilityModifier": 1.0
        },
        "Summer": {
          "AvailabilityModifier": 1.1
        },
        "Autumn": {
          "AvailabilityModifier": 1.0
        },
        "Winter": {
          "AvailabilityModifier": 0.8
        }
      }
    }
  ]
}
```

### 枚举定义
```json
{
  "ItemCategories": [
    "Mineral", "Plant", "Animal", "Food", "Tool", "Weapon", "Armor", "Accessory", "Material", "Consumable"
  ],
  "QualityLevels": [
    "Poor", "Common", "Fine", "Superior", "Masterwork", "Legendary", "Mythical"
  ],
  "RarityLevels": [
    "Common", "Uncommon", "Rare", "Epic", "Legendary", "Mythical"
  ]
}
```

---

## 🏘️ 部族配置 (TribeConfig.json)

### 数据结构
```json
{
  "Version": "1.0.0",
  "LastModified": "2024-01-01T00:00:00Z",
  "Tribes": [
    {
      "TribeID": "HanMajority",
      "Name": "汉族主支",
      "DisplayName": "汉族主支",
      "Description": "主体民族，分布于中原腹地，擅长农业、手工业、文化传承",
      "Region": "CentralPlains",
      "Population": {
        "Total": 20000000,
        "GrowthRate": 0.02,
        "AgeDistribution": {
          "Children": 0.25,
          "Adults": 0.65,
          "Elders": 0.10
        }
      },
      "Culture": {
        "Type": "Agricultural",
        "Values": ["Education", "Harmony", "Tradition", "Filial Piety"],
        "Traditions": [
          {
            "Name": "PoetryGathering",
            "Description": "诗会雅集",
            "Frequency": "Monthly",
            "Effects": {
              "CulturalInfluence": 0.1,
              "Education": 0.05
            }
          }
        ],
        "Language": "Classical Chinese",
        "Religion": "Confucianism"
      },
      "Specialties": [
        {
          "Type": "Agriculture",
          "Level": 4,
          "Bonus": 0.25
        },
        {
          "Type": "Handicraft",
          "Level": 3,
          "Bonus": 0.15
        },
        {
          "Type": "Education",
          "Level": 4,
          "Bonus": 0.20
        }
      ],
      "SocialStructure": {
        "Type": "Hierarchical",
        "Classes": [
          {
            "Name": "Scholars",
            "Percentage": 0.05,
            "Influence": 0.30
          },
          {
            "Name": "Farmers",
            "Percentage": 0.70,
            "Influence": 0.40
          },
          {
            "Name": "Artisans",
            "Percentage": 0.20,
            "Influence": 0.25
          },
          {
            "Name": "Merchants",
            "Percentage": 0.05,
            "Influence": 0.05
          }
        ]
      },
      "Economy": {
        "Primary": "Agriculture",
        "TradeGoods": ["Rice", "Silk", "Porcelain", "Tea"],
        "Currency": "Copper Coins",
        "WealthLevel": "Moderate"
      },
      "Technology": {
        "Level": 3,
        "Strengths": ["Agriculture", "Metallurgy", "Textiles"],
        "Weaknesses": ["Navigation", "Firearms"]
      },
      "Military": {
        "Strength": "Moderate",
        "Specialization": ["Infantry", "Crossbow"],
        "Fortifications": "Strong"
      },
      "Diplomacy": {
        "DefaultStance": "Neutral",
        "Relations": {
          "HakkaMinority": "Friendly",
          "NomadTribes": "Cautious",
          "SeaIslandPeople": "Trade"
        }
      },
      "CultivationRealms": {
        "Distribution": {
          "Primitive": 0.60,
          "Existence": 0.25,
          "Mastery": 0.12,
          "Transcendence": 0.025,
          "Sage": 0.005
        },
        "AdvancementRate": 1.0
      }
    }
  ]
}
```

---

## ⚙️ 系统参数配置 (SystemConfig.json)

### 数据结构
```json
{
  "Version": "1.0.0",
  "LastModified": "2024-01-01T00:00:00Z",
  "GameSettings": {
    "TimeFlow": {
      "RealToGameRatio": 60,
      "PauseOnMenu": true,
      "ContinueWhenOffline": true
    },
    "WorldSize": {
      "TotalPopulation": 100000000,
      "ActiveRegions": 5,
      "SimulationDepth": "High"
    }
  },
  "CultivationSystem": {
    "Realms": [
      {
        "RealmID": "Primitive",
        "Name": "原始境",
        "Level": 1,
        "Requirements": {
          "Virtue": 0,
          "Knowledge": 0,
          "Experience": 0
        },
        "Bonuses": {
          "VirtueGain": 1.05,
          "LearningSpeed": 1.10,
          "Focus": 1.05,
          "Lifespan": 2,
          "Perception": 1.05
        },
        "Abilities": ["BasicMeditation", "SimpleReflection"]
      },
      {
        "RealmID": "Existence",
        "Name": "存乎境",
        "Level": 2,
        "Requirements": {
          "Virtue": 100,
          "Knowledge": 50,
          "Experience": 1000
        },
        "Bonuses": {
          "VirtueGain": 1.10,
          "LearningSpeed": 1.20,
          "Focus": 1.15,
          "Lifespan": 5,
          "Perception": 1.15
        },
        "Abilities": ["EnhancedMeditation", "MoralInsight"]
      }
    ]
  },
  "QualitySystem": {
    "Levels": [
      {
        "QualityID": "Poor",
        "Name": "粗制品",
        "Multiplier": 0.7,
        "DurabilityRange": [50, 70],
        "PriceModifier": 0.6
      },
      {
        "QualityID": "Common",
        "Name": "普通品",
        "Multiplier": 1.0,
        "DurabilityRange": [80, 100],
        "PriceModifier": 1.0
      },
      {
        "QualityID": "Masterwork",
        "Name": "大师品",
        "Multiplier": 2.0,
        "DurabilityRange": [250, 300],
        "PriceModifier": 5.0
      }
    ]
  },
  "SeasonalSystem": {
    "Seasons": [
      {
        "SeasonID": "Spring",
        "Name": "春季",
        "Duration": 90,
        "GlobalEffects": {
          "PlantGrowth": 1.20,
          "GatheringEfficiency": 1.15,
          "CultivationBonus": 1.05
        },
        "SpecialProducts": ["SpringBambooShoot", "TenderLeaves"]
      }
    ]
  },
  "FirearmsTechnology": {
    "Eras": [
      {
        "EraID": "EarlyFirearms",
        "Name": "火器初兴",
        "TechLevel": 1,
        "AvailableWeapons": ["Matchlock", "EarlyCannon"],
        "ProductionDifficulty": 0.6,
        "SafetyRating": 0.7
      }
    ]
  }
}
```

---

## 🔧 C# 数据模型示例

### 地域配置模型
```csharp
public class RegionConfig
{
    public string Version { get; set; }
    public DateTime LastModified { get; set; }
    public List<Region> Regions { get; set; }
}

public class Region
{
    public string RegionID { get; set; }
    public string Name { get; set; }
    public string DisplayName { get; set; }
    public string Description { get; set; }
    public string RegionType { get; set; }
    public Climate Climate { get; set; }
    public Terrain Terrain { get; set; }
    public Resources Resources { get; set; }
    public Population Population { get; set; }
    public Culture Culture { get; set; }
    public Economy Economy { get; set; }
    public Dictionary<string, float> Modifiers { get; set; }
    public Dictionary<string, SeasonalEffect> SeasonalEffects { get; set; }
}

public class Climate
{
    public string Type { get; set; }
    public Dictionary<string, int> Temperature { get; set; }
    public Dictionary<string, int> Rainfall { get; set; }
    public List<string> Disasters { get; set; }
}
```

### 物品配置模型
```csharp
public class ItemConfig
{
    public string Version { get; set; }
    public DateTime LastModified { get; set; }
    public List<Item> Items { get; set; }
}

public class Item
{
    public string ItemID { get; set; }
    public string Name { get; set; }
    public string DisplayName { get; set; }
    public string Description { get; set; }
    public string Category { get; set; }
    public string SubCategory { get; set; }
    public Quality Quality { get; set; }
    public string Rarity { get; set; }
    public ItemProperties Properties { get; set; }
    public Dictionary<string, object> Attributes { get; set; }
    public List<ObtainMethod> ObtainMethods { get; set; }
    public Usage Usage { get; set; }
    public List<CraftingRecipe> CraftingRecipes { get; set; }
}

public class ItemProperties
{
    public float Weight { get; set; }
    public float Volume { get; set; }
    public int Durability { get; set; }
    public int StackSize { get; set; }
    public int BasePrice { get; set; }
}
```

---

## 🔧 Go 数据模型示例

### 地域配置模型
```go
type RegionConfig struct {
    Version      string    `json:"Version"`
    LastModified time.Time `json:"LastModified"`
    Regions      []Region  `json:"Regions"`
}

type Region struct {
    RegionID        string                     `json:"RegionID"`
    Name            string                     `json:"Name"`
    DisplayName     string                     `json:"DisplayName"`
    Description     string                     `json:"Description"`
    RegionType      string                     `json:"RegionType"`
    Climate         Climate                    `json:"Climate"`
    Terrain         Terrain                    `json:"Terrain"`
    Resources       Resources                  `json:"Resources"`
    Population      Population                 `json:"Population"`
    Culture         Culture                    `json:"Culture"`
    Economy         Economy                    `json:"Economy"`
    Modifiers       map[string]float64         `json:"Modifiers"`
    SeasonalEffects map[string]SeasonalEffect  `json:"SeasonalEffects"`
}

type Climate struct {
    Type        string            `json:"Type"`
    Temperature map[string]int    `json:"Temperature"`
    Rainfall    map[string]int    `json:"Rainfall"`
    Disasters   []string          `json:"Disasters"`
}
```

### 物品配置模型
```go
type ItemConfig struct {
    Version      string    `json:"Version"`
    LastModified time.Time `json:"LastModified"`
    Items        []Item    `json:"Items"`
}

type Item struct {
    ItemID           string                        `json:"ItemID"`
    Name             string                        `json:"Name"`
    DisplayName      string                        `json:"DisplayName"`
    Description      string                        `json:"Description"`
    Category         string                        `json:"Category"`
    SubCategory      string                        `json:"SubCategory"`
    Quality          Quality                       `json:"Quality"`
    Rarity           string                        `json:"Rarity"`
    Properties       ItemProperties                `json:"Properties"`
    Attributes       map[string]interface{}        `json:"Attributes"`
    ObtainMethods    []ObtainMethod                `json:"ObtainMethods"`
    Usage            Usage                         `json:"Usage"`
    CraftingRecipes  []CraftingRecipe              `json:"CraftingRecipes"`
}

type ItemProperties struct {
    Weight      float64 `json:"Weight"`
    Volume      float64 `json:"Volume"`
    Durability  int     `json:"Durability"`
    StackSize   int     `json:"StackSize"`
    BasePrice   int     `json:"BasePrice"`
}
```

---

## 📝 配置文件管理建议

### 文件组织结构
```
/Config/
├── SystemConfig.json          # 核心系统参数
├── GameSettings.json          # 游戏设置
├── Constants.json             # 常量定义
├── RegionConfig.json         # 地域配置
├── GeographyConfig.json      # 地理配置
├── ClimateConfig.json        # 气候配置
├── SeasonConfig.json         # 季节配置
├── ItemConfig.json           # 物品配置
├── LifeItemsConfig.json      # 生活用品配置
├── MaterialConfig.json       # 材料配置
├── ResourcesConfig.json      # 资源配置
├── EquipmentConfig.json      # 装备配置
├── QualitySystemConfig.json  # 品质系统配置
├── SkillConfig.json          # 技能配置
├── TribeConfig.json          # 部族配置
├── NPCConfig.json            # NPC配置
├── CultivationConfig.json    # 修身配置（包含境界系统）
├── Localization_zh-CN.json   # 中文本地化
└── Localization_en-US.json   # 英文本地化

### 版本控制
- 每个配置文件都包含版本号和最后修改时间
- 使用语义化版本控制 (Semantic Versioning)
- 重大更改时增加主版本号，向后兼容更改增加次版本号

### 验证机制
- 实现JSON Schema验证
- 添加数据完整性检查
- 提供配置文件验证工具

### 性能优化
- 大型配置文件考虑分片加载
- 实现配置缓存机制
- 支持热重载功能

---

## 🚀 使用示例

### C# 读取配置
```csharp
using System.Text.Json;

public class ConfigManager
{
    public static T LoadConfig<T>(string filePath)
    {
        var json = File.ReadAllText(filePath);
        var options = new JsonSerializerOptions
        {
            PropertyNameCaseInsensitive = true,
            ReadCommentHandling = JsonCommentHandling.Skip
        };
        return JsonSerializer.Deserialize<T>(json, options);
    }
}

// 使用示例
var regionConfig = ConfigManager.LoadConfig<RegionConfig>("Config/World/RegionConfig.json");
var centralPlains = regionConfig.Regions.FirstOrDefault(r => r.RegionID == "CentralPlains");
```

### Go 读取配置
```go
package config

import (
    "encoding/json"
    "io/ioutil"
    "time"
)

func LoadConfig[T any](filePath string) (*T, error) {
    data, err := ioutil.ReadFile(filePath)
    if err != nil {
        return nil, err
    }
    
    var config T
    err = json.Unmarshal(data, &config)
    if err != nil {
        return nil, err
    }
    
    return &config, nil
}

// 使用示例
regionConfig, err := LoadConfig[RegionConfig]("Config/World/RegionConfig.json")
if err != nil {
    log.Fatal(err)
}

for _, region := range regionConfig.Regions {
    if region.RegionID == "CentralPlains" {
        // 处理中原地区配置
        break
    }
}
```

---

## 📚 附录

### 常用枚举值
```json
{
  "RegionTypes": ["Agricultural", "Maritime", "Nomadic", "Forest", "Desert", "Mountain"],
  "ClimateTypes": ["Temperate", "Tropical", "Arid", "Continental", "Polar"],
  "QualityLevels": ["Poor", "Common", "Fine", "Superior", "Masterwork", "Legendary", "Mythical"],
  "RarityLevels": ["Common", "Uncommon", "Rare", "Epic", "Legendary", "Mythical"],
  "CultivationRealms": ["Primitive", "Existence", "Mastery", "Transcendence", "Sage"],
  "Seasons": ["Spring", "Summer", "Autumn", "Winter"],
  "ItemCategories": ["Mineral", "Plant", "Animal", "Food", "Tool", "Weapon", "Armor", "Accessory", "Material", "Consumable"]
}
```

### 数据类型映射
| JSON类型 | C#类型 | Go类型 | 说明 |
|---------|--------|--------|---------|
| string | string | string | 文本字符串 |
| number | int/float/double | int/float64 | 数值类型 |
| boolean | bool | bool | 布尔值 |
| array | List<T> | []T | 数组/切片 |
| object | class/Dictionary | struct/map | 对象/映射 |
| null | null | nil | 空值 |

### 最佳实践
1. **一致性**：保持命名和结构的一致性
2. **可扩展性**：设计时考虑未来扩展需求
3. **可读性**：添加适当的注释和描述
4. **性能**：避免过深的嵌套结构
5. **维护性**：定期检查和更新配置文件

---

> **注意**：本文档基于混沌世界游戏设定，提供标准化的JSON配置格式。开发者应根据实际需求调整具体实现细节。