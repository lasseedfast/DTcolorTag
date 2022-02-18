// Lets tags inherit the color of the parent tag.

/**
 * [Multiply list values with 65535. Else the colors will be close to black.]
 * @param  {list} olorArray [List from parent, values between 0-1.]
 * @return {list}     [List with values that works for DT.]
 */
function rgb(colorArray) {
    newColorArray = []
    colorArray.forEach(i => {
        newColorArray.push(65535 * i)
    });
    return newColorArray
};

(() => {
    const app = Application("DEVONthink 3");
    app.includeStandardAdditions = true;

    const selection = app.selectedRecords();

    selection.forEach(record => {
        if (String(record.parents.name()) !== 'Tags') { // Sort out nested tags.
            try {
                const parent = record.parents.uuid() // Get parents UUID.
                let parentRecord = app.getRecordWithUuid(String(parent)) // Get parent record.
                record.color = rgb(parentRecord.color()) // Assign the color of the parent to the tag.
            } catch (error) { console.log(error) };
        };

    })
})();
