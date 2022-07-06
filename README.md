# ExcessiveCore API Docs for developers
###### NOTES:
- Your plugin that hooks into the ExcessiveCore' API will never be able to, unless the 'API' section is set to 'true' in the 'config.yml' file of ExcessiveCore plugin.
- You are to access the api using the ExccessiveAPI class from the plugin.
- There is a way around it, if you want to bypass the 'API' boolean, you can access the methods from the classes inside the plugin itself as i made them intentionally public for urgent situations.
- You are able to set custom UUIDs etc... but you are not permitted to make the UUIDs intentionally readeable by the ingame users as this plugin is made specifically secure.
- Current accessible features: Currency, Ranks.

> Setup:
You just call the feature manager needed via a static method from the class called 'ExcessiveAPI' & that's it, you're all set.

> Currency:
```java
BankManager bankManager = ExcessiveAPI.getBankManager();

// Method examples...
bankManager.editPlayerBalance(player, 1.2, Operator.ADD);
instance.getLogger().info(player.getDisplayName() + ": " + bankManager.getCurrentCurrencySymbol() + bankManager.getBalance(player));
bankManager.setCurrencySymbol("€");
instance.getLogger().info(player.getDisplayName() + ": " + bankManager.getCurrentCurrencySymbol() + bankManager.getBalance(player));
```

> Ranks:
```java
RanksManager ranksManager = ExcessiveAPI.getRanksManager();

// Method examples...
                                          // new rank UUID   // new rank name // new rank displayname // rank permissions...
Rank newRank = ranksManager.createNewRank(UUID.randomUUID(), "exampleRank", "&c&lExampleRank", "server.gamemodes.join", "excessivecore.economy.currency");
instance.getLogger().info(newRank.getDisplayName() + ": " + ranksManager.getRankPermissions(newRank).toString());
ranksManager.clearPermissionsOfRank(newRank);
ranksManager.removeRank(newRank);
```

###### And many more methods you can choose from...
