# Creating printable TaskPaper 3 reports

_Captured: 2016-02-16 at 20:11 from [support.hogbaysoftware.com](http://support.hogbaysoftware.com/t/creating-printable-taskpaper-3-reports/1488)_

A draft example of a script which places a Due report (Markdown with some HTML color tags) in the clipboard, so that you can view/print it from a [Marked 22](http://marked2app.com/) clipboard preview.

Sample output, (JavaScript for Automation source below).

(This report groups items by due date. They are sorted, within day headings, by any time component of the @due(dateTime) tag in that item. Tags other than @due are displayed in the text, which is preceded by the project title, as well as any specific time).

![](http://support.hogbaysoftware.com/uploads/db8375/optimized/1X/52350222cf07917b72046129c3f390a6dc0a4539_1_458x500.png)[ Screen shot 2016-02-16 at 00.22.59.png631x688 115 KB ](http://support.hogbaysoftware.com/uploads/db8375/original/1X/52350222cf07917b72046129c3f390a6dc0a4539.png)

> _// DUE REPORT script for TaskPaper 3 Preview ver 0.01_
    
    
    
    var strClip = (function () {
        'use strict';
    
        function fnTP3Context(editor, options) {
    
        // concatMap ::  [a] -> (a -> [b]) -> [b]
        function concatMap(xs, f) {
            return [].concat.apply([], xs.map(f));
        }
    
        function itemProject(item) {
            var p = item.parent;
    
            while (p) {
                if (p.getAttribute('data-type') === 'project') {
                    var strTrail = p.attributes.trailingMatch;
    
                    return strTrail ? p.bodyString.slice(
                        0, -(strTrail.length)
                    ) : p.bodyString;
                };
                p = p.parent;
            }
            return '';
        }
    
        function timePart(item, strTimeTag) {
            var strDate = item.getAttribute('data-' + strTimeTag);
    
            return strDate ? strDate.slice(10)
                .trim() : '';
        }
    
        function otherTags(lstAttribNames, attribs, strGroup) {
            return concatMap(
                    lstAttribNames,
                    function (k) {
                        var strTag = k.indexOf(
                                'data-'
                            ) === 0 ? k.slice(5) :
                            '',
                            strValue = attribs[k];
    
                        // Non-grouping tag attributes included
                        return (
                            strTag && ['type', strGroup]
                            .indexOf(strTag) === -1
                        ) ? [
     				'@' + strTag + (strValue ? '(' + strValue + ')' : '')
    			     ] : [];
                        }
                    )
                    .join(' ');
            }
    
            var outline = editor.outline;
    
    
        // READING OF SORT SPEC
        var lstOrder = options.orderBy.split(/\s+/),
            strSortBy = lstOrder[0].trim(),
            blnZA = (lstOrder.length > 1) && (lstOrder[1].trim()
                .substr(0, 4)
                .toLowerCase() === 'desc'),
            strSortAttrib = 'data-' + strSortBy;
    
    
        // READING OF GROUPING SPEC
        var lstGroup = options.groupBy.split(/\./),
            strGroup = lstGroup[0],
            strGroupAttrib = 'data-' + strGroup,
            strGroupFn = lstGroup.length > 1 ? lstGroup[1] : undefined,
    
    
            // FILTERED BY ...
            lstFiltered = outline.evaluateItemPath(options.filter),
    
            // GROUPED BY ...
            dctGroups = lstFiltered.reduce(
                function (groups, dctItem) {
                    var v = dctItem.attributes[strGroupAttrib],
                        vGroup = strGroupFn ? eval(
                            '"' + v.toString() + '".' + strGroupFn
                        ) : v,
                        dctGroup = groups[vGroup] || {};
    
                    dctGroup[dctItem.id] = dctItem;
                    groups[vGroup] = dctGroup;
    
                    return groups;
                }, {}
            ),
    
            // GROUPS ORDERED BY
            lstGroups = Object.keys(dctGroups)
            .sort(blnZA ?
                function (a, b) {
                    return a === b ? 0 : (a < b ? 1 : -1);
                } : function (a, b) {
                    return a === b ? 0 : (a > b ? 1 : -1);
                });
    
        return "### <font color='silver'>" + strGroup.charAt(0)
            .toUpperCase() + strGroup.slice(1) + "</font>\n\n" +
            lstGroups.map(function (k) {
                var dctGroup = dctGroups[k];
    
                return "#### <font color=gray>" + k.substr(0, 7) +
                    '</font>&nbsp;<font color=red>' + k.slice(8) +
                    '</font>\n' + Object.keys(dctGroup)
                    .map(function (id) {
                        var item = dctGroup[id],
                            attribs = item.attributes;
    
                        var strTime = timePart(item, strGroup),
                            strProject = itemProject(item),
    
                            strPrefixes = (strTime ?
                                '<font color=gray><b>' +
                                strTime +
                                '</font></b>\t' :
                                '') + (strProject ?
                                '<font color=gray>' +
                                strProject +
                                '</font>&nbsp;' : '');
    
    
                        return strPrefixes +
                            // body text
                            item.bodyString.slice(
                                2, -attribs.trailingMatch.length
                            )
                            // Any remaining (non-grouping) tags
                            + ' <font color=gray>' + otherTags(
                                item.attributeNames,
                                attribs,
                                strGroup
                            ) + '</font>';
                    })
                    .sort()
                    .join('\n');
            })
            .join('\n\n');
    }
    
    var ds = Application("TaskPaper")
        .documents,
        varResult = ds.length ? ds[0].evaluate({
            script: fnTP3Context.toString(),
            withOptions: {
                filter: '//@due',
                groupBy: 'due.substr(0, 10)',
                orderBy: 'due'
            }
        }) : false;
    
    return varResult;
    })();
    
    
    var a = Application.currentApplication(),
        sa = (a.includeStandardAdditions = true, a);
    
    sa.setTheClipboardTo(strClip);
    
    strClip
