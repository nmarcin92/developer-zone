# B-L462E-CELL1/TYPE1SC

Integrate your B-L462E-CELL1 Discovery kit board along with the TYPE 1SE module with built-in eSIM (ST4SIM-200M).

## Prerequisites

- The B-L462E-CELL1/TYPE1SC board with a USB cable.
- Installed **STM32CubeIDE**.
- Installed **minicom** (for Linux) or RealTerm (for Windows) or other serial communication program.
- A user with access to the Coiote IoT Device Management platform.

## Step 1: Cloning the Anjay freeRTOS client repository

Enter the command line interface on your machine and paste the following command:

   ```
   git clone --recursive https://github.com/AVSystem/Anjay-freertos-client
   ```

## Step 2: Compiling the board

0. Connect the B-L462E-CELL1/TYPE1SC board to a USB port of your machine.
0. Go to the STM32CubeIDE.
0. Import the project cloned in the previous step to your workspace:
    - From the navigation bar, select **File** and click **Import**.
    - From the **General** list, select **Existing Projects into Workspace** and click **Next**.
    - In **Select root directory**, indicate the catalog containing the cloned Anjay freeRTOS client repository.
    - In the **Projects** field, select **Anjay-freertos-client-B-L462E-CELL1-TYPE1SC** and click **Finish**.
    ![Import project](images/import.PNG "Import project")
0. In the Project Explorer, navigate to the **Anjay-freertos-client-B-L462E-CELL1-TYPE1SC** project:
    - Right-click on the project name and select **Build Project**. The build should take less than one minute to complete.
    - After the build is finished, right-click on the project name, select **Run As** and click the **1 STM32 Cortex-M C/C++ Application** option.
        - In the **Lauch Configuration Selection**, choose the **Anjay-freertos-client-B-L462E-CELL1-TYPE1SC** option and click **OK**.
0. After the build and run are complete, the board is now compiled.

## Step 3: Configuring the Client

1. With the board still connected to a serial port interface, open a serial communication program.
2. Press the reset button located on the board. This should trigger the following prompt:

    ``Press any key in 3 seconds to enter config menu...``

3. Press any key and in the configuration menu, change the default credentials to your data by following the instructions presented in the program and save it .
      ![Client configuration](images/config_menu.png "Client configuration")

## Step 4: Connecting to the LwM2M Server

To connect to Coiote IoT Device Management LwM2M Server, please register at https://www.avsystem.com/try-anjay/.

To connect the board:

1. Log in to Coiote DM and from the left side menu, select **Device Inventory**.
2. In **Device Inventory**, click **Add device**.
3. Select the **Connect your LwM2M device directly via the Management server** tile.
       ![Add via Mgmt](images/mgmt_tile.png "Add via Mgmt")
    3. In the **Device credentials** step:
         - In the **Device ID** enter your board endpoint name, e.g. `test_device`.
             ![Device credentials step](images/add_mgmt_quick.png "Device credentials step")
         - In the **Security mode** section, select the **PSK** mode:
              - In the **Key identity** field, type `test_device`
              - In the **Key** field, type the shared secret used in the device-server authentication.  
    4. Click the **Add device** button and **Confirm** in the confirmation pop-up.
    5. In the **Connect your device** step, wait for the board to connect.
    6. Click **Go to device** to see your added device dashboard.
        ![Registered device](images/registered_device.png "Registered device")
