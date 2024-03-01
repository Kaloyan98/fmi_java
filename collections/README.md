Data Structures in Java (Collections)
Smart City Hub
We will create a global system for storing information about all smart devices installed in a given city, called SmartCityHub.

It will provide the ability to:

Register and unregister smart devices.
Retrieve and sort smart devices based on a specific criterion.
SmartDevice
The devices that can be installed in cities are:

🚥 SmartTrafficLight
💡 SmartLamp
📹 SmartCamera
They should implement the SmartDevice interface:

package bg.sofia.uni.fmi.mjt.smartcity.device;

public interface SmartDevice {
    String getId();
    String getName();
    double getPowerConsumption();
    LocalDateTime getInstallationDateTime();
    DeviceType getType();
}

Each device should have a mandatory constructor with parameters (String name, double powerConsumption, LocalDateTime installationDateTime).

Two devices are considered equal if their IDs match.

DeviceType
Device types are represented by an enum with values TRAFFIC_LIGHT, LAMP, and CAMERA.

package bg.sofia.uni.fmi.mjt.smartcity.enums;

public enum DeviceType {
    TRAFFIC_LIGHT("TFL"),
    LAMP("LM"),
    CAMERA("CM");

    private final String shortName;

    private DeviceType(String shortName) {
        this.shortName = shortName;
    }

    public String getShortName() {
        return shortName;
    }
}

ID
The ID of each device is constructed as follows: <short name of device type>-<device name>-<unique number per device type>, where the number is incremented by 1 (starting from 0) for each creation of a device of a specific type.

SmartCityHub
Create the SmartCityHub class:

package bg.sofia.uni.fmi.mjt.smartcity.hub;

public class SmartCityHub {
    public SmartCityHub() {}

    public void register(SmartDevice device) throws DeviceAlreadyRegisteredException {
        throw new UnsupportedOperationException();
    }

    public void unregister(SmartDevice device) throws DeviceNotFoundException {
        throw new UnsupportedOperationException();
    }

    public SmartDevice getDeviceById(String id) throws DeviceNotFoundException {
        throw new UnsupportedOperationException();
    }

    public int getDeviceQuantityPerType(DeviceType type) {
        throw new UnsupportedOperationException();
    }

    public Collection<String> getTopNDevicesByPowerConsumption(int n) {
        throw new UnsupportedOperationException();
    }

    public Collection<SmartDevice> getFirstNDevicesByRegistration(int n) {
        throw new UnsupportedOperationException();
    }
}

To calculate the elapsed time between two LocalDateTime objects, use the java.time.Duration class and specifically the java.time.Duration.between(...) method.

Performance
Note that a city may have thousands or even millions of installed devices. Your solution should efficiently handle large amounts of data.
