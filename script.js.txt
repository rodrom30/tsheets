document.addEventListener("DOMContentLoaded", function () {
    const form = document.getElementById("timeSheetForm");
    const canvas = document.getElementById("signature-pad");
    const ctx = canvas.getContext("2d");
    const clearBtn = document.getElementById("clear-signature");

    let drawing = false;

    canvas.addEventListener("mousedown", (e) => {
        drawing = true;
        ctx.beginPath();
        ctx.moveTo(e.offsetX, e.offsetY);
    });

    canvas.addEventListener("mousemove", (e) => {
        if (drawing) {
            ctx.lineTo(e.offsetX, e.offsetY);
            ctx.stroke();
        }
    });

    canvas.addEventListener("mouseup", () => (drawing = false));
    clearBtn.addEventListener("click", () => ctx.clearRect(0, 0, canvas.width, canvas.height));

    form.addEventListener("submit", function (e) {
        e.preventDefault();

        const name = document.getElementById("name").value;
        const date = document.getElementById("date").value;
        const startTime = document.getElementById("startTime").value;
        const endTime = document.getElementById("endTime").value;
        const materials = document.getElementById("materials").value;
        const signature = canvas.toDataURL(); // Convert signature to image

        alert("Form submitted! (Next step: Connect to Google Sheets or Email)");

        // Here, you can add code to send data to Google Sheets or EmailJS
    });
});
