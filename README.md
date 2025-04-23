# party-planer

let party = {};
let guests = [];

function savePartyDetails() {
  const date = document.getElementById("party-date").value;
  const description = document.getElementById("party-description").value;
  const message = document.getElementById("invite-message").value;

  if (!date || !description || !message) {
    alert("Please fill out all fields!");
    return;
  }

  party = { date, description, message };

  document.getElementById("display-date").textContent = party.date;
  document.getElementById("display-description").textContent = party.description;
  document.getElementById("display-message").textContent = party.message;

  document.getElementById("party-details").style.display = "block";
  document.getElementById("rsvp-section").style.display = "block";
  document.getElementById("guest-list-section").style.display = "block";
}

function registerGuest() {
  const name = document.getElementById("name").value.trim();
  const surname = document.getElementById("surname").value.trim();

  if (!name || !surname) {
    alert("Please enter both name and surname!");
    return;
  }

  guests.push({ name, surname });
  updateGuestList();
  document.getElementById("name").value = "";
  document.getElementById("surname").value = "";
}

function updateGuestList() {
  const list = document.getElementById("guest-list");
  list.innerHTML = "";

  guests.forEach((guest, index) => {
    const li = document.createElement("li");
    li.textContent = `${index + 1}. ${guest.name} ${guest.surname}`;
    list.appendChild(li);
  });
}

