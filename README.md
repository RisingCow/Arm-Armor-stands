# Arm Armor Stands (Paper 26.2)

This is the **source project**, not a precompiled JAR. It targets Paper 26.2 and Java 25.

## Features
- Crafting recipe for one unique writable book:
  - top row: Diamond | Stick | Diamond
  - middle row: Book | empty | empty
  - bottom row: empty | empty | empty
- The recipe is removed after the first successful craft and the `book-created` flag is saved in `plugins/ArmArmorStands/data.yml`.
- Right-click the book to open an online-player GUI, then a cause-selection GUI.
- The chosen action is scheduled for 30 seconds later; cooldown is 180 seconds from confirmation.
- New and currently loaded armor stands are given arms.
- The visible book name and lore can be edited in `plugins/ArmArmorStands/config.yml`.
- No player commands are registered and no public chat announcements are sent.

## Important limitations
- This project has not been compiled or run in this environment because it only has Java 21 and no Maven/network access. Paper 26.2 requires Java 25. Do not treat it as tested until the build and in-game checks pass.
- The unique-item state intentionally stays `true` after the book is lost or administratively deleted, so the recipe will not recreate another copy.
- The delayed action requires the selected target to still be online after 30 seconds.
- As with any Bukkit/Paper plugin, server owners can inspect plugin files and logs. This plugin does not attempt to hide from administrators or undo administrative deletion.

## Build
Requires JDK 25 and Maven 3.9+.

```bash
mvn clean package
```

The resulting JAR should be `target/Arm-Armor-stands.jar`.

## Build online with GitHub Actions
1. Upload the contents of this project to a new GitHub repository.
2. Open the repository's **Actions** tab.
3. Select **Build plugin** and click **Run workflow** (or push to `main`).
4. Open the completed run and download the `Arm-Armor-stands` artifact. It contains the JAR if compilation succeeds.

## Install
1. Stop your Paper 26.2 server.
2. Upload `Arm-Armor-stands.jar` into the server's `plugins` folder.
3. Start the server and check the console for errors.
4. Test on a disposable test server first, not on a server with a world you care about.
