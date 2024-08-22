class EVChargingStation:
    def __init__(self, station_id, name, location, available_slots):
        self.station_id = station_id
        self.name = name
        self.location = location
        self.available_slots = available_slots

    def display_info(self):
        print(f"Station ID: {self.station_id}")
        print(f"Name: {self.name}")
        print(f"Location: {self.location}")
        print(f"Available Slots: {self.available_slots}")

class EVChargingStationFinder:
    def __init__(self):
        self.stations = []

    def add_station(self, station):
        self.stations.append(station)

    def find_stations(self, location=None, min_slots=0):
        results = []
        for station in self.stations:
            if (location is None or location.lower() in station.location.lower()) and station.available_slots >= min_slots:
                results.append(station)
        return results

    def display_stations(self, stations):
        for station in stations:
            station.display_info()
            print("-" * 30)

class SlotBooking:
    def __init__(self, finder):
        self.finder = finder

    def book_slot(self, station_id):
        station = next((s for s in self.finder.stations if s.station_id == station_id), None)
        if station:
            if station.available_slots > 0:
                station.available_slots -= 1
                print(f"Slot booked successfully at {station.name}!")
            else:
                print("No slots available at this station.")
        else:
            print("Station not found.")


station1 = EVChargingStation(station_id=1, name="EV Station 1", location="Downtown", available_slots=5)
station2 = EVChargingStation(station_id=2, name="EV Station 2", location="Uptown", available_slots=2)
station3 = EVChargingStation(station_id=3, name="EV Station 3", location="Midtown", available_slots=0)

finder = EVChargingStationFinder()
finder.add_station(station1)
finder.add_station(station2)
finder.add_station(station3)


print("Finding stations with available slots in 'Downtown':")
stations = finder.find_stations(location="Downtown", min_slots=1)
finder.display_stations(stations)

print("\nBooking a slot at Station 1:")
booking = SlotBooking(finder)
booking.book_slot(1)

print("\nFinding stations with at least 1 slot available:")
stations = finder.find_stations(min_slots=1)
finder.display_stations(stations)
