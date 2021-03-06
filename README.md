# happyscribe-to-anki

`happyscribe-to-anki` is a command-line utility to export transcript data from https://www.happyscribe.com/ for use with Anki decks containing the following four fields: Sentence, Translation, Notes, Audio.

## Pre-requisites

- The audio files should be placed into the Anki media directory. On macOS, this is `~/Library/Application Support/Anki2/Me/collection.media/`
- These audio files should have the exact same name as what was uploaded to Happy Scribe.

## To run

1. Add your Happy Scribe API key to config.json
2. Run `node app.js` to retrieve the transcript IDs which represent each transcript
3. Run `node app.js` again to use the IDs to create an export
4. Run `node app.js <EXPORT_ID>` to download and extract the transcripts from a ZIP file.
5. Run `node app.js csv <OUTPUT_DESTINATION>` to convert the transcripts to a CSV file.
6. Import into Anki

## Notes

- To re-run with new data, you will need to manually remove the `/output` directory as well as the `transcript_ids.json` file.

- At present there is an occasional issue with Step 3, where it will fail to locate the download URL. Waiting a minute or so, or simply repeating Step 3 until it works, are workarounds for the time being.

## Future improvements

- Allow users to specify their own Anki deck format. At present the implementation is quite rigid as it requires the aforementioned four fields in your deck.

- Remove the need to supply arguments for Step 5. Instead have the output directory added to `config.json` and test for the existence of files in the `output/json` directory.

- Optionally have the `output/` directory and the `translation_ids.json` files removed once the CSV file has been generated.

- Have the app eventually run in its entirety from a single command.
