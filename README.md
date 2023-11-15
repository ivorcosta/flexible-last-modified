# Test on localhost
1. Run `./gradlew bootRun`
2. Run `curl -I localhost:8080`
3. Working: The `Last-Modified` is 2023 and not 1980

# Test with java 17 (bugged)
1. Edit `build.grade`, change `project-id` with the id of your app engine flexible project
2. Run `./gradlew appengineDeploy`
3. Grab your deploy version URL in the console and change the next command
4. Run `curl -I https://20231115t133951-dot-project-id.ue.r.appspot.com`
5. Bug: The `Last-Modified` should be 2023 and not 1980

# Test with java 8 (not bugged)
1. Edit `app.yaml`, comment `runtime_config` section with java 17 and uncomment the one with java 8
2. Edit `build.grade`, comment `sourceCompatibility` and `targetCompatibility` with java 17 and uncomment the ones with java 8
3. Run `./gradlew appengineDeploy`
4. Grab your deploy version URL in the console and change the next command
5. Run `curl -I https://20231115t135745-dot-project-id.ue.r.appspot.com`
6. Working: The `Last-Modified` is 2023 and not 1980