# How MOSFET Arrays Can Prevent Current Leakage in High-Voltage Systems

_Captured: 2017-12-23 at 17:30 from [www.allaboutcircuits.com](https://www.allaboutcircuits.com/news/how-mosfet-arrays-balance-supercapacitor-cells/)_

High-voltage systems now have the choice of using plug-and-play PCBs to automatically control leakage current in backup power circuitry.

There is a growing application of multiple supercapacitor cells in modules that serve the energy-storage needs of higher-voltage systems in datacenters, industrial automation equipment, and public utility infrastructure. But these high-voltage systems often demand safe voltage balancing.

That's because differences in leakage currents between individual supercapacitors result in changes in voltages, and overvoltage is a major cause of failures in supercapacitors. That can cause reduced lifespan and eventual failure since exceeding the maximum voltage on a supercapacitor leads to cell failure.

Therefore, designers need to balance supercapacitor cells in a stack of two or more to overcome overvoltage-related issues.

Enter plug-and-play PCBs that provide a platform for balancing high-voltage supercapacitors through a low-voltage, low-leakage, and low-current controlling method in a small form factor.

When there is an increase in the supercapacitor voltage caused by leakage current from another supercapacitor, it causes a decrease in the RDS(ON) of the MOSFET connected to the supercapacitor. And that increases the current, IDS(ON), and reduces the voltage.

The plug-and-play boards use MOSFET arrays to offer a circuit design that is more efficient than other passive or active balancing methods as it offers lower cost and takes smaller design space. These MOSFET boards automatically control leakage current and enhance the reliability of backup devices like 700V systems.

##### ![](https://www.allaboutcircuits.com/uploads/articles/Figure_1_-_SABMB9100_board_-_ALD.jpg)

> _The schematic of a fully-populated board with three MOSFET arrays that serve four supercapacitors: C1 to C4. Image courtesy of_

##### _[Advanced Linear Devices Inc. (ALD)](http://www.aldinc.com/)._

Take, for instance, the MOSFET boards from Advanced Linear Devices Inc. (ALD) shown above, which balance for 2.8V, 3.0V and 3.3V supercapacitors arranged in a series stack by equalizing the leakage current of each cell.

The ALD SABMB810028 boards are built with the company's [ALD810028SCLI SAB MOSFETs](http://www.aldinc.com/ald_precision-supercap-auto-balancing-sab-mosfets.php), which balance each cell through low levels of leakage current without exposure to supercapacitor charge/discharge voltage levels for cells of 3,000 Farad (F) or more.

##### ![](https://www.allaboutcircuits.com/uploads/articles/SABMB810025.jpg)

> _A view of the plug-and-play board with MOSFET arrays. Image courtesy of_

These boards allow supercapacitor cell charging and discharging currents to pass through the cells, themselves, directly. This bypasses SAB MOSFETs mounted on the board with near zero additional leakage current. It ensures that the average additional power dissipation due to DC leakage of the supercapacitor is zero.

It also makes them a viable alternative to methods where additional power dissipation used by the circuitry far exceeds the supercapacitor energy burn caused by leakage currents. So this method of supercapacitor balancing is highly energy-efficient and is well suited for low-loss energy harvesting and long life battery-operated applications.

The boards--rated for -40°C to +85°C temperatures--can balance up to four supercapacitors connected in series when fully populated. Moreover, populated boards are available with different combinations of MOSFETs to reach required voltages.
