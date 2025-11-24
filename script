let port, writer;

async function connect() {
  port = await navigator.serial.requestPort();
  await port.open({ baudRate: 115200 });
  writer = port.writable.getWriter();
  alert("Connected to Arduino!");
}

document.getElementById("connectBtn").onclick = connect;

function send(cmd) {
  if (writer) writer.write(new TextEncoder().encode(cmd + "\n"));
}

function linkSlider(id, label, prefix) {
  const el = document.getElementById(id);
  const lbl = document.getElementById(label);
  el.oninput = e => {
    lbl.textContent = e.target.value + "°";
    send(prefix + e.target.value);
  };
}

linkSlider("base", "bVal", "B:");
linkSlider("shoulder", "sVal", "S:");
linkSlider("elbow", "eVal", "E:");
linkSlider("wrist", "wVal", "W:");
linkSlider("gripper", "gVal", "G:");
