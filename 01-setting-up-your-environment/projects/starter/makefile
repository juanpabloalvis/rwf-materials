PACKAGES := $(wildcard packages/*)
FEATURES := $(wildcard packages/features/*)
BUILD-RUNNER := packages/fav_qs_api packages/key_value_storage

print:
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo %%F)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo %%P)

pods-clean:
	rm -Rf ios/Pods ; \
	rm -Rf ios/.symlinks ; \
	rm -Rf ios/Flutter/Flutter.framework ; \
	rm -Rf ios/Flutter/Flutter.podspec ; \
	rm ios/Podfile ; \
	rm ios/Podfile.lock ; \


get:
	flutter pub get
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo Updating dependencies on %%F & flutter pub get)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Updating dependencies on %%P & flutter pub get)

upgrade:

	flutter pub upgrade
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo Updating dependencies on %%F & flutter pub upgrade)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Updating dependencies on %%P & flutter pub upgrade)


lint:
	flutter analyze

format:
	flutter format --set-exit-if-changed .

testing:
	flutter test
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo Running test on %%F & flutter pub test)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Running test on %%P & flutter pub test)

test-coverage:
	flutter test --coverage
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo Running test on %%F & flutter test --coverage)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Running test on %%P & flutter test --coverage)

clean:
	flutter clean
	for /D %%F in ("packages/features/*") do (cd "%cd%\packages\features\%%F" & echo Running clean on %%F & flutter clean)
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Running clean on %%P & flutter clean)

build-runner:
	for /D %%P in ("packages/*") do (cd "%cd%\packages\%%P" & echo Running build-runner on %%P & flutter pub run build_runner build --delete-conflicting-outputs)
